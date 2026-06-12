---
title: "Ayuda sin internet en ubuntu"
date: 2010-09-22
forum: General Help
---

### Post by Raarias on 2010-09-22
ayer instale Ubuntu 10.04, pero por alguna extraña razon no puedo entrar a internet.

lo instale en una particion, por que tambien tengo xp ya que la compu no es solo mia, y todo parecia perfecto, pero cuando intento conectarse a internet me sale un mensaje que dice que el cable de red no esta conectado.

lo curioso es que si esta conectado, y en Windows, que es de donde escribo en estos momentos no hay ningun problema, y no se que hacer estoy desesperado, por que nunca me habia pasado esto



QUE hago?????



P.S.
aqui estan los datos de la coneccion

Dirección física: 00-1C-C0-BC-0D-2C
Dirección IP: 163.178.95.90
Máscara de subred: 255.255.255.192
Puerta de enlace predeterminada: 10.178.4.129
Servidores DNS: 163.178.88.2, 163.178.170.24
Servidor WINS:

---

### Post by DeMus on 2010-09-22
I hope somebody from your country reads this and he can help you. You have posted on an English speaking forum and probably not many people speak your language. Can you try to translate your message, maybe we can help you then.

---

### Post by bodhi.zazen on 2010-09-22
These forums are primarily English. 

Please use the appropriate LoCo Forums or irc channel for faster support.

Otherwise you will have to wait for someone who understands your post (sorry about that).

---

### Post by petrasflorin on 2010-09-22
he's saying that he has windows xp and just installed ubuntu 10.04 but he has no internet connection in ubuntu.

he still has windows xp and the internet on that works just fine as you can see he's on this forum from xp.

his question is: why isn't ubuntu recognizing his wired connection ?

edit: no, I'm not spanish, I don't speak spanish. I just understand it because of similar native language. Romanian.

---

### Post by BobVila on 2010-09-22
[I]I understand the post, but haven't tried to speak spanish in several years. I'll give it a crack to at least get the ball rolling.

OP installed Ubuntu yesterday. Ubuntu's telling him the network cable is unplugged, but it's working fine in windows. The network details he posted are the standard output from Windows' networking dialog box.[/I]

Raarias,
No he escribido en espanol por un rato; disculpame. 

Esta usando DHCP en Windows?

Si entras esto en el terminal cuando esta usando Ubuntu, que dice?
```
ifconfig
```

Puede ser que Ubuntu no ha detectado eth0...

---

### Post by Raarias on 2010-09-22
the [COLOR=#000000]translation is very well done[/COLOR]


yes am using DHCP in windows and [COLOR=#000000]let me start ubuntu to see what he says [/COLOR][COLOR=#000000]when I'm writing ifconfig[/COLOR]

---

### Post by Raarias on 2010-09-22
root@transportes:/home/transportes# ifconfig
 eth0      Link encap:Ethernet  direcciónHW 00:1c:c0:bc:0d:2c  
 Dirección inet6: fe80::21c:c0ff:febc:d2c/64 Alcance:Enlace  ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
 Paquetes RX:26 errores:0 perdidos:0 overruns:0 frame:0
 Paquetes TX:6 errores:0 perdidos:0 overruns:0 carrier:0
 colisiones:0 long.colaTX:1000 
    RX:1788 (1.7 KB)  TX bytes:468 (468.0 B)     Interrupción:27 Dirección base: 0xe000 
  
  
 lo        Link encap:Bucle local  
 Direc. inet:127.0.0.1  Másc:255.0.0.0
 Dirección inet6: ::1/128 Alcance:Anfitrión
 ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
 Paquetes RX:12 errores:0 perdidos:0 overruns:0 frame:0
 Paquetes TX:12 errores:0 perdidos:0 overruns:0 carrier:0  colisiones:0 long.colaTX:0 
 Bytes RX:720 (720.0 B)  TX bytes:720 (720.0 B)



[FONT=&quot]


[/FONT]

---

### Post by BobVila on 2010-09-22
*I'll type this in english this time. If you need me to try to translate something, let me know.*

So the system detected eth0 ok, it's just not obtaining an IP address via DHCP. 

Just as a test, try entering the settings you've taken from Windows into the manual configuration for eth0 in Ubuntu.

Also, enter the following into the command line and see if the system is producing any dhcp errors during bootup:

```
less /var/log/messages
```

---

### Post by Raarias on 2010-09-22
[COLOR=#000000]I try to enter the options that Windows has taken the manual settings for eth0 in Ubuntu but still have problems

[/COLOR]and I wrote and I came out the following




Sep 20 17:14:32 transportes kernel: imklog 4.2.0, log source = /proc/kmsg started.
Sep 20 17:14:32 transportes rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="591" x-info="http://www.rsyslog.com"] (re)start
Sep 20 17:14:32 transportes rsyslogd: rsyslogd's groupid changed to 103Sep 20 17:14:32 transportes rsyslogd: rsyslogd's userid changed to 101
Sep 20 17:14:32 transportes kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep 20 17:14:32 transportes kernel: [    0.000000] Initializing cgroup subsys cpu
Sep 20 17:14:32 transportes kernel: [    0.000000] Linux version 2.6.32-24-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 (Ubuntu 2.6.32-24.39-generic 2.6.32.15+drm33.5)
Sep 20 17:14:32 transportes kernel: [    0.000000] KERNEL supported cpus:
Sep 20 17:14:32 transportes kernel: [    0.000000]   Intel GenuineIntel
Sep 20 17:14:32 transportes kernel: [    0.000000]   AMD AuthenticAMD
Sep 20 17:14:32 transportes kernel: [    0.000000]   NSC Geode by NSC
Sep 20 17:14:32 transportes kernel: [    0.000000]   Cyrix CyrixInstead
Sep 20 17:14:32 transportes kernel: [    0.000000]   Centaur CentaurHauls
Sep 20 17:14:32 transportes kernel: [    0.000000]   Transmeta GenuineTMx86
Sep 20 17:14:32 transportes kernel: [    0.000000]   Transmeta TransmetaCPU
Sep 20 17:14:32 transportes kernel: [    0.000000]   UMC UMC UMC UMC
Sep 20 17:14:32 transportes kernel: [    0.000000] BIOS-provided physical RAM map::

---

