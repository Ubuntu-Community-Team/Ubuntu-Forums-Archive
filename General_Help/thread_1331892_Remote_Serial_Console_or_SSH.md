---
title: "Remote Serial Console or SSH?"
date: 2009-11-19
forum: General Help
---

### Post by Nekativ on 2009-11-19
I have a setup that uses two transceivers that basically act just like a serial cable. 

What I am wondering is if there is the possibility to setup a SSH host that runs through a serial/usb cable.

The serial console works and I am able to use putty to access the file system however, at times it seems to have some unstability, and what I am curious of is (if it is possible) weather SSH is more stable than a remote serial console.

Also SSH seems to have more options and utilities than the remote serial console. The option I am most interested in is the ability to transfer files. Although there really isn't much that I know about remote serial consoling so there is probably a way I am unaware of.

If you have any advice/links/material about SSH or Remote Serial console I would love to know.

---

### Post by juancarlospaco on 2009-11-19
If it have an IP address you can SSH them, if not you cant.

---

### Post by efflandt on 2009-11-19
With a serial console you have no error checking, so a wiring or other glitch might or might not be noticed.  File transfer is possible, but somewhat different from network transfers (long time since I have done that).

To use ssh, scp, etc. you need networking, and the way you do that over serial is pppd or  similar.  That is how networking is done on Bluetooth which is a pseudo serial connection (I have done that between Palm TX and mRouter in Windows).  It is also similar to dial up networking, except you do not actually dial and therefore no dial up app or modem commands necessary.

Depending upon what docs you have on your system, web search **linux serial howto** and **linux pppd howto**.

Something to note is that even though ssh is encrypted, it can use compression.  So file transfer can actually be faster than your connection depending upon the type of data being sent (regular files compress more than zip or gzip files).

Back in the days, I also used to do networking over Laplink parallel cables using plip.

---

### Post by Nekativ on 2009-11-20
> **efflandt said:**
> With a serial console you have no error checking, so a wiring or other glitch might or might not be noticed.  File transfer is possible, but somewhat different from network transfers (long time since I have done that).

To use ssh, scp, etc. you need networking, and the way you do that over serial is pppd or  similar.  That is how networking is done on Bluetooth which is a pseudo serial connection (I have done that between Palm TX and mRouter in Windows).  It is also similar to dial up networking, except you do not actually dial and therefore no dial up app or modem commands necessary.

Depending upon what docs you have on your system, web search **linux serial howto** and **linux pppd howto**.

Something to note is that even though ssh is encrypted, it can use compression.  So file transfer can actually be faster than your connection depending upon the type of data being sent (regular files compress more than zip or gzip files).

Back in the days, I also used to do networking over Laplink parallel cables using plip.

Thanks for the help, I will try to setup a network.

---

### Post by Nekativ on 2009-11-21
Well I have played around with various how-to's for setting up ppp connections for serial use, and I think I found the right guide:

[http://nst.sourceforge.net/nst/docs/scripts/null-modem-ppp.html](http://nst.sourceforge.net/nst/docs/scripts/null-modem-ppp.html)

However, I have a problem that I would assume is simple but I can't figure out. I cannot seem to figure out the local IP of linux to be used with the serial connection.

I use "ifconfig" but this is what I get and I do not really know the right one to use for the serial connection:

```
eth0      Link encap:Ethernet  HWaddr 00:22:15:2e:d1:d2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fbfc0000-fc000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:b6:98:06  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:feb6:9806/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3041 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:854647 (854.6 KB)  TX bytes:233838 (233.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-B6-98-06-62-36-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


Also if anyone would like to suggest better, simpler, or even different ways of setting up PPP for direct serial lines, please share your experience.

---

### Post by Nekativ on 2009-11-21
bump

---

### Post by Nekativ on 2009-11-22
Well I finally managed to get a PPP network running, but I want to create something like a getty and I cannot seem to figure out how to translate this to be used with Upstart in ubuntu instead of inittab.

> **2.2. A getty-like installation of pppd**

 You can have the PPP daemon (pppd) start when you boot the system and have it monitor the serial line of your choice. An elegant way of achieving this is to edit the "/etc/inittab" file. This file contains information for initializing the system. Add the following to this file: 





[COLOR=#000000]# Start pppd for the serial laplink.
pd:2345:respawn:/usr/sbin/pppd /dev/ttyS1 nodetach
   [/COLOR]


    
This reads as follows: for runlevels 2, 3, 4 and 5 start "/usr/sbin/pppd /dev/ttyS1 nodetach" and if it dies (at the end of a connection) respawn (start a new one). The "nodetach" option makes that pppd stays connected to the terminal that started it, rather than forking and exiting. This option is necessary because the "init" process would respawn a new one immediately otherwise. Other entries in the inittab file specify getty processes to run on serial terminals (tty's); their initialization looks a lot like this one. 
    To activate this new configuration type:

```

[COLOR=#000000][root@griis /root]# /sbin/init q[/COLOR]
```

---

### Post by Nekativ on 2009-11-22
bump

---

