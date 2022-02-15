# PROXY SQUID
Conexion VPN por medio de proxy squid

# Instalacion del servicio PROXY SQUID

# INICIO:

sudo su

cd 

apt-get install squid -y && apt-get install squid3 -y

# Descargar e Instalar Archivos Necesarios:

* opnedns ( ubicar en carpeta "/etc" )
* payloads ( ubicar en carpeta "/etc" )
* squid.conf ( ubicar en carpeta "/etc/squid/" )

# Link de Descarga:

wget https://www.dropbox.com/s/gvpn6prfodxocfm/Pack_Squid.zip && unzip Pack_Squid.zip && mv opendns payloads /etc && rm -r /etc/squid/squid.conf && mv squid.conf /etc/squid


# Editar el Archivo squid.conf:

* usar NANO ó VIM

* vim /etc/squid.conf

* nano /etc/squid.conf

#CACHE DO SQUID
cache_mem 200 MB

maximum_object_size_in_memory 32 KB

maximum_object_size 1024 MB

minimum_object_size 0 KB

cache_swap_low 90

cache_swap_high 95

cache_dir ufs /var/spool/squid 100 16 256

access_log /var/log/squid/access.log squid

#ConfiguracaoSquiD

acl url1 dstdomain -i 192.168.1.10 #Aqui Poner su IP

acl url2 dstdomain -i 127.0.0.1

acl url3 url_regex -i '/etc/payloads'

acl url4 url_regex -i '/etc/opendns'

acl url5 dstdomain -i localhost

acl all src 0.0.0.0/0

http_access allow url1

http_access allow url2

http_access allow url3

http_access allow url4

http_access allow url5

http_access deny all


#portas

http_port 8080


#nome

visible_hostname xhokitope


via off

forwarded_for off

pipeline_prefetch off


# Editar Las Siguiented Lineas:

* PONER SU IP:

acl url1 dstdomain -i 192.168.1.10 

* Cambiar por su IP ejemplo 192.168.1.230

* Resultado acl url1 dstdomain -i 192.168.1.230

* PONER PUERTOS A USAR:

http_port 8080 #Cambiar por el puerto a usar

* Puede Agregar mas Puertos Ejemplo:

http_port 8080

http_port 3128


# Guardar El Archivo:

* NANO:

[CONTROL] + [X] yes [ENTER]

* VIM:

[ESCAPE] + :wq + [ENTER]

# Reiniciar el Servicio SQUID:

* service squid restart

# Detener el Servicio SQUID:

* service squid stop

# Iniciar el Servicio SQUID:

* service squid start

# Revizar el Servicio SQUID:

* service squid status

# Revizar Los Puertos y Servicios Activos:

* netstat -tnlp

* Compatible con Ubuntu 14, 16, 18

* NUNCA DEJES DE APRENDER

* @XhokitoPe

