---
title: "cant start tftp"
date: 2006-05-22
forum: General Help
---

### Post by jeisma on 2006-05-22
hello!

im using atftpd, i cant start the service.

running netstat -anp | grep ":69" returns nothing.

what could be missing in my system?

i have this line in my /etc/inetd.conf file:

tftp            dgram   udp     wait    nobody /usr/sbin/tcpd /usr/sbin/in.tftpd --tftpd-timeout 300 --retry-timeout 5     --mcast-port 1758 --mcast-addr 239.239.239.0-255 --mcast-ttl 1 --maxthread 100 --verbose=5  /tftpboot


thanks!

---

### Post by FeestBijtje on 2006-05-22
Ubuntu has install support with TFTP as you can read on the following link:
[http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install](http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install)

TFTP is ment to be no harm to others ive used in the past TFTP to send packets to other people but i hope this is ment for whole other things.

---

### Post by sysko on 2006-07-22
Make sure you have the **Internet super server** installed. In my case, on this installation anyways, Dapper LTS 6.06 did not install the inetd deamon by default (maybe I marked OFF during system installation, go figure!) 

/etc/inetd.conf was present though and I added the following line to it:

tftp            dgram   udp     wait    nobody  /usr/sbin/tcpd  /usr/sbin/in.tftpd /srv/tftp

... but without the inetd super deamon running (... not installed!) this was kinda useless.

To install the inetd deamon via Synaptic look for the following package:
**inetutils-inetd**

or from the command line
[PHP]sudo apt-get install inetutils-inetd[/PHP]

Once inetd got installed, it reads it's config file and the tftp was brough on-line automatically.

A little  
[PHP]netstat -anp | grep ":69"[/PHP]
returned a running tftp service on udp port 69

Hope this might help.

Comments, questions, insults ?

---

### Post by Euan17 on 2007-09-05
hey, im having trouble finding out if tftp server is actually running, i tried:
```
netstat -anp | grep ":69"  
``` but it didnt return anything.

i have installed tftpd-hda and installed inetutils-inetd (i already had something that conflicted so i removed that before installing i think it was called openbsd-inet or something like that)

when i type tftp in the console the promt changes to tftp> and asks me what to connect to so i give it the ip of the tftp client and try using "put" to send the file but it times out. when i try and use "get" from the client it says permission denied.

as you might be able to guess im new to linux and i dont have much of a clue about what im doing.

any help would be great

thanks

---

### Post by davidgarcin on 2007-11-21
Euan17 - Try this how-to, I found it quite useful, even if it didn't ultimately work for me (it worked for eveyone else though)

[http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/](http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/)

-Dave

---

