---
title: "Internet doesnt work"
date: 2010-07-05
forum: General Help
---

### Post by kleinempfaenger on 2010-07-05
Hi, I have a problem with my internet connection. It works on Windows with the same computer, but since an actualization of Lucid some days ago Ubuntu doesnt connect.
I tried to reinstall the network manager from a .deb package, but it says that there is a problem with "libnm-glib-vpn". So I downloaded this package, but couldnt install it. There were problems with dependencies. What can I do?

---

### Post by mike555 on 2010-07-05
more info is needed ......... what type of Internet are you trying to get? dsl by ethernet cable? dialup ? or USB ?

---

### Post by irv on 2010-07-05
Is it a wireless or wire connection? Do you have anything in your Network Connections under Wired or Wireless? Go to System > Preference > Network Connections.
[ATTACH]162546[/ATTACH]

---

### Post by kleinempfaenger on 2010-07-05
ethernet cable, router, dsl. Internet works fine on my laptop with lucid and on my desktop computer with windows. The problem is with Lucid on my desktop computer. Maybe since the last automatic update.

---

### Post by irv on 2010-07-05
A couple more things to check/post (from a terminal):
sudo lshw -C network
ifconfig -a

I will be off line but maybe someone will be able to help after you post the results.

---

### Post by kleinempfaenger on 2010-07-11
irv and others, I did what you told me and my results are the following:
First 
sudo lshw -C network:

  *-network DISABLED      
       description: Ethernet interface
       product: VT6105/VT6106S [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 86
       serial: 00:19:5b:6c:01:27
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: irq:5 ioport:b000(size=256) memory:ed000000-ed0000ff memory:10000000-1000ffff(prefetchable)


Second
ifconfig -a:

eth0      Link encap:Ethernet  direcciónHW 00:19:5b:6c:01:27  
          DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:5 Dirección base: 0xc000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:261 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:261 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:25704 (25.7 KB)  TX bytes:25704 (25.7 KB)


I see that my network is disabled, but I don't know why. Where could I activate it?

---

### Post by irv on 2010-07-12
If you right mouse click on the Network icon in the panel then select enable Network.

---

### Post by kleinempfaenger on 2010-07-14
Irv, thank you so much for your help. 
But still I haven't found a way to reactivate my internet connection. I don't have the icon on the panel. I also can't add it, because it doesn't appear in the list which appears after right click on the panel. Is there another way to add it?
Greetings, kl

---

### Post by irv on 2010-07-14
Go to your Synaptic Packager Manager and make sure “Network-Manager”, Network-Manager-PPTP-Gnome”, Network-Manager-Gnome” are installed.
System> Administration> Synaptic Package Manage.
[ATTACH]163441[/ATTACH]

---

### Post by kleinempfaenger on 2010-07-23
Irv, I got it. Thanks again for your help. The solution was very simple. The "notification area" was turned off and I searched for the network manager in the list.
Greetings, kleinempfaenger

---

