# Exam 3

**Nombre:** Luis Alejandro Tróchez  

**Código:** A00054648

**Enlace repositorio:** https://github.com/zehcort/so-exam3


## Desarrollo

## 3 y 4.

En el siguiente informe se explicará y evidenciará el funcionamiento de una red donde funcionan varios servidores, acompañado de tecnologías que facilitan la mediación entre los clientes y estos, permitiendo que no se genere sobre carga sobre servicios que proveen más máquinas en la misma red y que estas estén desocupadas.

Con tal objetivo, se hace uso de un servidor que cumple con la función de descubrir qué servicios se ofrecen dentro de la red (servidor Discovery Service) y otro encargado de que, una vez conocidos estos servicios prestados, los clientes que los soliciten hagan uso de ellos de manera equitativa ( balanceador de carga). Para el balanceo se utilizó el método de roundrobin, el cual reparte en orden natural al servidor (primero al 1, lugo al 2, luego al 3, y así hasta volver a iniciar)

De esta manera, en el momento en que el cliente solicite un servicio, este va a ser intermediado por los servicios mencionados por anterioridad, mas no por el servidor que provee el servicio que solicita. Para entender esto mejor, la manera como el balanceador de carga se da cuenta de los servidores existentes se da gracias al uso del reporte que hacen estos al servidor de discovery service, llamado consul templates. El registro de estos en la topología montada se realiza automáticamente.

Para demostrar el funcionamiento se utilizaron 5 máquinas, donde dos de ellas servían como los servidores de discovery service y de balanceador de carga, respectivamente. Junto a ello se desplegaron el las otras 3 máquinas un microservicio web (cada uno con un mensaje diferente para evidenciar el funcionamiento del balanceador; estos equipos que a su vez sirvieron de clientes para demostrar el funcionamiento de las tecnologías implementadas.

En primer lugar se mostrará el montaje de uno de los servidores de microservicios web, donde se hizo uso de un archivo en python y las tecnologías de flask y consul.



![][1]

![][2]

![][3]



Posterior a esto se motrarán algunas capturas del funcionamiento del balanceador de cargas. En ellas se evidencia el balanceador corriendo y la configuración del consul, así como la automatización de la inclusión de los servicios reportados por el discovery service.



![][4]

![][5]

![][6]

Después de esto, se mostrará el servicio prestado por el servidor discovery service. En el se incluyen los logs generados durante su estado activo, así como el resultado del consul members, comando que reporta qué agentes (servidores) hay activos durante la red.


![][7]

![][8]


Para finalizar, se muestran los servicios web corriendo después de la solicitud de los clientes, una vez fue procesada de la manera que se explicó en principio.

![][9]

![][10]

![][11]



## 5.

Para dar mayor escalabilidad a la red, al agregarse un nuevo microservicio a la misma, se podría contar con un API-Gateway, tecnología la cuál tiene como función codificar los servicios que se prestan y poder prestarlos de manera más eficiente cuando sean solicitados. Así pues, si existen 4 servidores en la red que prestan el mismo servicio, estos puedan unificar su operación y el cliente al solicitar sólo tenga que hacer la consulta a dicho API.

Por otro lado, a continuación se explican otros conceptos interesantes para la gestión eficiente de nuevos microservicios y su escalabilidad:

Protocolo de publicador/suscriptor: Es la metodología implementada en este informe, a través de la cuál todos los reportes de los servicios son centralizados a una máquina, en nuestro caso el discovery service.

Reactive Paradigm: En este, una vez se encuente que un microservicio está directamente relacionado con otro, así como que uno utilice el resultado del otro, se hará uso de la programación reactiva para facilitar un desenvolvimiento rápido de toda la cadena.









[1]: 1.PNG
[2]: 2.PNG
[3]: 3.PNG
[4]: 4.PNG
[5]: 5.PNG
[6]: 6.PNG
[7]: 7.PNG
[8]: 8.PNG
[9]: 9.PNG
[10]: 10.PNG
[11]: 11.PNG
