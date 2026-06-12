---
title: "puertos ttyS convertilos a ip"
date: 2009-11-19
forum: General Help
---

### Post by melcocha_ on 2009-11-19
hola
tengo un problema
tengo un iso lector de tarjetas que se conecta al server por medio del puerto ttyS y en el server tengo un programa que se encarga de ir a asociar las tarjetas a los puertos ttys y asi leer los codigos de las tarjetas que son los necesito transmitir via web.
 hasta ahi todo va bien el problema pasa cuando todos los usuarios le piden los codigos a las tarjetas al mismo tiempo el iso no sabe que hacer y pone en espera a algunos usuarios mientras libera la carga, bueno pense en  conseguir un comserver es un convertidor de rs232 a ethernet de un lado conectas cualquier cosas db9 y del otro sale ethernet esto para darle mas velocidad de transferencia a los datos que necesito con esto resulevo la perdida de paquetes que me solicitan mis usuarios conectados al server .
aqui es donde esta el problema, radica en que el programa encargado de leer los codigos de las tarjetas solo sabe leer los puertos ttyS y ahora con el comserver ya no esta el iso conectado al server si no que se conecto al router  directamente y ahora ya no usa un puerto ttyS si no que ahora usa una ip .
bueno he pensado en hacer unos puertos ttyS virtuales y esos mismo puertos virtuales redireccionarlos con la ip que me asigno mi router pero no se si se pueda hacer lo que quiero o si hay una manera mas facil de hacer por eso la ayuda haber si alguien sabe como hacerle o me orintan aqui dejo el link del comserver que tengo gracias de antemano.
[http://www.moxa.com/product/NPort_5210.htm](http://www.moxa.com/product/NPort_5210.htm)

---

