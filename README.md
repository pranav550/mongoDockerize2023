#pull image
docker pull mongo:latest

########## Repeat start #############
#run container
docker run --rm -d -p 27017:27017 --name mongo-container -e MONGO_INITDB_ROOT_USERNAME=root -e MONGO_INITDB_ROOT_PASSWORD=secret mongo:latest

#check runing container
docker ps

#Go inside the container
docker exec -it mongo-container /bin/sh

#go inside shell
mongosh -u root -p secret

show dbs
use blog

db.products.insertOne({name:'Mackbook'})
db.products.find()
exit
exit
########## Repeat end #############
docker stop mongo-container

##Rerun( From Reapeat start to Repeat End )

#check default folder for mongdb
docker inspect mongo
docker stop mongo-container

####volume

docker run --rm -d -p 27017:27017 --name mongo-container -e MONGO_INITDB_ROOT_USERNAME=root -e MONGO_INITDB_ROOT_PASSWORD=secret -v mongoData:/data/db mongo:latest

#volume list
docker volume ls

#volume remove
docker volume remove mongodata

#another way to create volume
docker run --rm -d -p 27017:27017 --name mongo-container -e MONGO_INITDB_ROOT_USERNAME=root -e MONGO_INITDB_ROOT_PASSWORD=secret -v %cd%:/data/db mongo:latest
