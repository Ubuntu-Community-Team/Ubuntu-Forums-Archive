---
title: "localhost page cannot be displayed"
date: 2011-05-02
forum: General Help
---

### Post by antpruitt on 2011-05-02
ubuntu natty vers

re: ampache, apache, apache2

I've tried untinstalling and reinstalling the package for ampache.  

I still cannot get localhost/ampache to display in my browser.  I can't even get localhost to display in my browser.  I've tried checking around in config files to see if i have ports open for listening. (i'm a noob at all of this)

My router has the port open that i specified.  on code -  service apache2 start i get:

(..Address already in use: make_sock: could not bind to address 192.168.1.65:8000
no listening sockets available, shutting down


I can't find any other config files. I don't know what else to do with the amapche installation. (which included an install of mysql-server package, even tho i NEVER got a prompt to enter in root passwd for the mysql db.)

Any thoughts on where i should start?  I've banged around forums for a while and still have not found a solution.  Currently using dhcp.  

etc/network/interfaces code =

auto lo
iface lo inet loopback





auto eth0
iface eth0 inet dhcp
~                      

ifconfig = 

eth0      Link encap:Ethernet  HWaddr 00:11:11:6a:fb:93  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:11ff:fe6a:fb93/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:91093562 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110012889 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1771218634 (1.7 GB)  TX bytes:3201090521 (3.2 GB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:223880 errors:0 dropped:0 overruns:0 frame:0
          TX packets:223880 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30247470 (30.2 MB)  TX bytes:30247470 (30.2 MB)


thanks to all.

---

### Post by antpruitt on 2011-05-03
[FONT=&quot]Found the /etc/apache2 directory and then found saw the ports.conf file.  Changed the virtualhost line to include localhost:80


Think i'm good now.

thnx, tho.

[/FONT]

---

