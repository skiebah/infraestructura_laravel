## Conexión de red entre contenedores de diferentes entornos.

### Entorno Docker-Project

Detectar el nombre del adaptador de red de un contenedor.

```shell

docker inspect <nombre_o_id_contenedor> | jq '.[0].NetworkSettings.Networks | keys'

#------ OUTPUT -------
#[
#  "db_default",
#]
#---------------------


# ----- ADD ADAPTER -----

docker network connect <network-name> <contenedor-name>

```

Luego de agregar el adaptador de red podemos establecer conexiones entre los contenedores.

#### RECOMENDACIONES
Incluir el adaptador de los docker de infraestructura en los docker del proyecto y no viceversa, de manera que los contenedores de infraestructura posean un unico adaptador de RED.

---
## Creación de Volumen:

```shell

#docker volume create --name=<name volume>

docker volume create --name=dbdata-prod

```