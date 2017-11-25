## Miniproyecto Sistemas Operativos

**Universidad ICESI**  
**Curso:** Sistemas Operativos  
**Docente:** Daniel Barragán C.  
**Tema:**  Servicios web  
**Correo:** daniel.barragan at correo.icesi.edu.co  
  
**Estudiante:**  Juan Camilo Swan  
**código:**  A00054620  
**Correo:** juan.swan at correo.icesi.edu.co  

**ulr:** https://github.com/juanswan13/so-project

## Objetivos
* Desplegar una aplicación en un servidor que ejecuta el sistema operativo Linux
* Realizar los ajustes y depuración necesarios para desplegar una
aplicación en Linux
* Realizar aplicaciones para obtener información del sistema operativo

## Descripción
Para el despliegue de una aplicación en un servidor se requiere conocer los procedimientos necesarios relacionados con la configuracion de las interfaces de red, ajustes de seguridad, instalación de dependencias, usuarios y herramientas de depuracíon del sistema operativo.

El siguiente proyecto consiste en el despliegue de una aplicación web para obtener información del sistema operativo (La aplicación debe permitir consulta uso de CPU, memoria y espacio en disco). Para este propósito se debe emplear el sistema operativo Ubuntu Server 16.04, el microframework flask y ambientes virtuales.

<p align="center">
  <img src="images/vista-despliegue.png" alt="webservice architecture"/>
</p>

## Actividades
* Nombre y código de todos los integrantes del grupo (máximo 3) (5%)
* Ortografía y redacción (5%)
* Descripción breve de los pasos para cumplir con lo solicitado
  * Sistema operativo Ubuntu Server 16.04 (10%)
  * Configuración de interfaces de red (10%)
  * Configuración de puertos (10%)
  * Instalación de dependencias (10%)
  * Creación de ambientes virtuales (10%)
  * Aplicación en Python (10%)
  * Validación de la ejecución del servicio (netstat) (10%)
* Pruebas de la solución a través de capturas de pantalla. Puede emplear si lo desea una herramienta de captura de pantalla a formato .gif (10%)
* El informe debe ser entregado en formato pdf a través del moodle y el informe en formato README.md debe ser subido a un repositorio de github. El repositorio de github debe ser un fork de https://github.com/ICESI-Training/so-project y para la entrega deberá hacer un Pull Request (PR) respetando la estructura definida. El código fuente y la url de github deben incluirse en el informe (10%).  
  
## Desarrollo

**1.** Para el desarrollo de la actividad propuesta se tuvo que realizar la instalación del sistema operativo Ubuntu Server 16.04 sobre el cual se realizó el despliegue de toda la solución. Inicialmente se tuvo que instalar el servicio SSH sobre la maquina virtual para poder realizar una conexión a esta misma desde Putty y realizar el desarrollo de la actividad con más facilidad. 

**Inicio de Ubuntu Server 16.04 y activación del servicio SSH.**  
  ![][1]  
  
**2.** Ahora que se encuentra activo el servicio SSH, se debe configurar las interfaces de red. Para esto se tiene que asignar una IP a la interfaz de red y luego levantar la interfaz (de una vez es recomendable abrir puertos que después van a ser utilizados), para esto se deben ejecutar los siguientes comandos:  
```
$ ip addr add 192.168.1.17/24 dev enp0s3
$ nmcli con up enp0s8
$ sudo ufw disable
$ ipp addr
```  
  ![][2]  

Una vez estos aspectos estén configurados, se puede realizar una conexión por medio del Putty a la maquina Ubuntu Server para empezar a desarrollar la actividad.  
  
**3.**  Una vez se ha realizado la conexión SSH al servidor, se empieza el desarrollo del proyecto instalando todas las dependencias necesarias para el funcionamiento del servidor. Para esto se debe realizar la creación de un ambiente virtual sobre el cual se va a realizar la instalación de una versión flask de pip sobre la que va a correr el servicio especificado. Para realizar la instalación de las dependencias necesarias se deben usar los siguientes comandos:  
  * Instalacion de pip  
```
$ sudo apt-get install python3-pip
$ sudo pip3 install virtualenv 

```  
  * Creación y activación del ambiente virtual 
```
$ virtualenv proyectoFinal
$ source proyectoFinal/bin/activate 
```  
  * Instalación de Flask sobre el ambiente virtual
```
$ pip install flask
$ vi operation.py
```  
  ![][3]  

**4.** En este momento ya se encuentran instaladas todas las dependencias necesarias y también se está ubicado dentro del ambiente virtual que fue instalado y al que le fue implementado el microframework Flask. Es decir que el paso a seguir es realizar la aplicación en python que se va a encargar de resolver el problema propuesto para el proyecto (obtener información del sistema operativo). Para resolver este problema se ha ideado que se puede utilizar los comandos del sistema encargados de dar dicha información, tomar sus resultados y exponerlos al cliente que realiza la consulta HTTP. Dicho desarrollo se muestra a continuación.
  ![][4]  
  
**5.** En este punto se debe poner en ejecución el microservicio. Una vez el microservicio este ejecutándose, ya se habrá solucionado la problemática del proyecto y ya se podrá realizar consultas HTTP al microservicio para conocer información del sistema en cualquier momento. Para ejecutar el microservicio se debe utilizar el siguiente comando:
```
$ python operation.py
```  
  ![][5]  
  
**6.** Por último, ya con el servicio funcionando, se realiza la validación del servicio. Para esto se ha realizado una demostración donde se hace uso del servicio desde una terminal de consola en la misma red del servidor. La IP del servidor es 192.168.1.17 ejecutando el servicio por el puerto 5000 y la dirección IP de la otra terminal con la que se realizan las pruebas es 192.168.1.20. 
Demostración del funcionamiento:
  ![][6]  
  
 **La conexión con el servicio en 192.168.1.17:5000 está activa**
  ![][7]  
   
 **Se puede visualizar la información del sistema**
  ![][8]   

  
## Referencias
* https://www.ubuntu.com/download/server  
* https://github.com/ICESI/so-discovery-service  
* https://help.ubuntu.com/community/SSH/OpenSSH/Configuring  
* https://gist.github.com/farhadurfahim/73c0fad6350332cef7a653bcd762f08d  
* https://openwebinars.net/blog/20-comandos-linux-imprescindibles-para-sysadmin/  
* https://www.solvetic.com/tutoriales/article/3871-como-guardar-resultado-comando-en-archivo-texto-linux/  
* http://recursospython.com/guias-y-manuales/lectura-y-escritura-de-archivos/  
* http://www.thegeekstuff.com/2009/10/how-to-capture-unix-top-command-output-to-a-file-in-readable-format  


[1]: images/MaquinaUbuntuServer.PNG
[2]: images/interfacesDeRed.PNG
[3]: images/ServerEnviroment.PNG
[4]: images/microservicioEncargadoDeLaAplicacion.PNG
[5]: images/aplicacionWebCorriendo.PNG
[6]: images/IPcliente.PNG
[7]: images/netstat.PNG
[8]: images/ConsolaAccediendo.PNG
