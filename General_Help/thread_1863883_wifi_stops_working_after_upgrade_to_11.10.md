---
title: "wifi stops working after upgrade to 11.10"
date: 2011-10-18
forum: General Help
---

### Post by camilomusic on 2011-10-18
Help please!

I just upgraded to Ubuntu 11.10 and my wireless card doesn't seem to be working. I go to the top right corner and there are no available connections shown, as if the card was turned off.
What can I do to solve this problem?

My laptop is an Easynote NJ32, and my card is, I think an RalinkRT2700E

And this also may be of some work:


camilo@camilo-EASYNOTE-NJ32:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

camilo@camilo-EASYNOTE-NJ32:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:23:8b:c1:3a:c9  
          Direc. inet:192.168.2.4  Difus.:192.168.2.255  Másc:255.255.255.0
          Dirección inet6: fe80::223:8bff:fec1:3ac9/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:7200 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:6352 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:6384211 (6.3 MB)  TX bytes:1076440 (1.0 MB)
          Interrupción:18 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:112 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:112 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:8712 (8.7 KB)  TX bytes:8712 (8.7 KB)

The wired network is working fine, the problem is with the wireless.

Thanks!

---

