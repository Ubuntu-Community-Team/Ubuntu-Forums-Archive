---
title: "Dual Ip assignment"
date: 2006-02-21
forum: General Help
---

### Post by mjunior on 2006-02-21
Guys, I need to have access to two different networks at the same NIC. So I need help to find a way to set differents IP and gateways for them...


Already tried to do sudo ifconfig <new Ip assignment> eth0:1
but when I do ping the destination is unreachable cause I need a new gateway to the other network..By the way, when I do reboot the ifconfig assignment is gone...any clue??

Already tried to staiteful add a route to the new network by: sudo toute add -net <destination net> <netmask> <newgateway for the new net> eth0:0
but still have no ping

Using gui or gedit to set directly at etc/network/interfaces , I have ping to both nets when I set the related IPs separatly

Any help is welcomed..

---

### Post by dcstar on 2006-02-22
[QUOTE=mjunior]Guys, I need to have access to two different networks at the same NIC. So I need help to find a way to set differents IP and gateways for them...
.......[/QUOTE]
This may be of assistance:

[http://www.unixshell.com/forum/showthread.php?t=371](http://www.unixshell.com/forum/showthread.php?t=371)

As far as the gateway goes, just adding the right route should suffice.

---

### Post by mjunior on 2006-02-22
Tks David,

I saw the link you sent and its pretty much what I have at my file:
mapping hotplug
	script grep
	map eth0

# New IP assignment
iface eth0:1 inet static
address 192.168.53.100
netmask 255.255.0.0

# Original IP assignment
iface eth0 inet static
address 192.168.24.80
netmask 255.255.0.0
gateway 192.168.24.1

auto eth0
auto eth0:1

iface ppp0 inet ppp
provider ppp0


The symptom I described at the previous post "..By the way, when I do reboot the ifconfig assignment is gone...any clue??" now desapear..
I had forgot to put the line: auto eth0:1 

So far I can only reach the net 192.168.24.0

Aditional info:

route:
marcelojunior@mjunior:~$ route
Tabela de Roteamento IP do Kernel
Destino         Roteador        MáscaraGen.    Opções Métrica Ref   Uso Iface
192.168.0.0     *               255.255.0.0     U     0      0        0 eth0
default         192.168.24.1    0.0.0.0         UG    0      0        0 eth0
marcelojunior@mjunior:~$

ifconfig:
marcelojunior@mjunior:~$ ifconfig
eth0       Encapsulamento do Link: Ethernet  Endereço de HW 00:50:EB:0E:30:BF
          inet end.: 192.168.24.80  Bcast:192.168.24.255  Masc:255.255.0.0
          endereço inet6: fe80::250:ebff:fe0e:30bf/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          RX packets:2734 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1207 errors:0 dropped:0 overruns:0 carrier:0
          colisões:0 txqueuelen:1000
          RX bytes:1261601 (1.2 MiB)  TX bytes:193282 (188.7 KiB)
          IRQ:22 Endereço de E/S:0xd400

eth0:1     Encapsulamento do Link: Ethernet  Endereço de HW 00:50:EB:0E:30:BF
          inet end.: 192.168.53.100  Bcast:192.168.53.255  Masc:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          IRQ:22 Endereço de E/S:0xd400

lo         Encapsulamento do Link: Loopback Local
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          RX packets:3526 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3526 errors:0 dropped:0 overruns:0 carrier:0
          colisões:0 txqueuelen:0
          RX bytes:948324 (926.0 KiB)  TX bytes:948324 (926.0 KiB)

Please, any help is welcomed..

---

### Post by mjunior on 2006-02-22
Tks David,

Adding the line below the problem was solved:
up route add -net 192.168.53.0/24 gw 192.168.53.254

---

### Post by dcstar on 2006-02-23
[QUOTE=mjunior]Tks David,

I saw the link you sent and its pretty much what I have at my file:
mapping hotplug
	script grep
	map eth0

# New IP assignment
iface eth0:1 inet static
address 192.168.53.100
netmask **255.255.0.0**

# Original IP assignment
iface eth0 inet static
address 192.168.24.80
netmask **255.255.0.0**
gateway 192.168.24.1
......[/QUOTE]
Be warned that these netmasks are not Class C, and you may well have trouble as both those IP addresses are now on the same subnet.

If you really want it to work, I'd use a 255.255.255.0 mask.

---

### Post by mjunior on 2006-02-23
I'm aware, but thanks for remind me anyway. I need both nets beeing broadcasted by my pc :-k  

One last question...

about the final script line I added " up route add -net 192.168.53.0/24 gw 192.168.53.254"
isn't that the same as adding the sudo if config add route -net 192.168.53.0 netmask 255.255.255.0 gw 192.168.53.254 ??

also bothers me the fact that applying this command the route showing (comand sudo route) desapear on the reboot...

:confused:

---

