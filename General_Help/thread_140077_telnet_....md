---
title: "telnet ..."
date: 2006-03-05
forum: General Help
---

### Post by mach5 on 2006-03-05
i have my mail server configured in ubuntu, and is listening to default ports ie. 110 and 25. but telnet isnt able to access it. i.e it give error Network not found to local host.. 

what is the exact problem, and how it can be resolved !

---

### Post by dcstar on 2006-03-05
[QUOTE=mach5]i have my mail server configured in ubuntu, and is listening to default ports ie. 110 and 25. but telnet isnt able to access it. i.e it give error Network not found to local host.. 

what is the exact problem, and how it can be resolved ![/QUOTE]
Telnetd is not installed as default, install it.

---

### Post by skymt on 2006-03-05
[QUOTE=dcstar]Telnetd is not installed as default, install it.[/QUOTE]
He's trying to connect to his mail server, using the telnet client as a generic TCP client. Netcat is better for that, so I'd recommend installing that instead.

And as for the problem, it's "localhost", not "local host".

---

### Post by schilcha on 2006-03-06
[QUOTE=mach5]what is the exact problem, [...]![/QUOTE]

That's a good question indeed! 

Please let us know, 
what you want to do (personally talk to your smtpd?), 
how did you do that (by using telnet -- what command did you use?) and
what error-messages did you get?

So, after all, here's how it works on my system:
> 
$ telnet localhost 25
Trying 127.0.0.1...
Connected to smithers.springfield.
Escape character is '^]'.
220 localhost.localdomain ESMTP Postfix (Ubuntu)
quit
221 Bye
Connection closed by foreign host.
$


---

### Post by schilcha on 2006-03-06
Just one more guess... is your loopback device up? Exec the command "ifconfig" and look for a section like this:
> 
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27416 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9682328 (9.2 MiB)  TX bytes:9682328 (9.2 MiB)


---

### Post by mach5 on 2006-03-07
i think u told the partial solution of my prob..
i i have a dsl connection

and my ifconfig look like this

eth0      Link encap:Ethernet  HWaddr 00:08:5C:5D:07:17
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:5cff:fe5d:717/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1238 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1323 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:947844 (925.6 KiB)  TX bytes:214549 (209.5 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:59.144.141.130  P-t-P:203.101.126.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:1206 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:935683 (913.7 KiB)  TX bytes:183391 (179.0 KiB)


there is no localhost stuff here !!

---

### Post by schilcha on 2006-03-07
Have a look at the file /etc/network/interfaces. In mine, there's a lo-related section right at the beginning:
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

[...]

You definitely need this, so your lo-interface is configured at startup.

---

### Post by mach5 on 2006-03-07
it is there in the file named interfaces...

but still there is not loopback

when m disconnected.. my ifconfig gives me a blank output :(

---

### Post by schilcha on 2006-03-07
What, if you try activating lo manually? Try
```
sudo ifup lo
```
Please post any error/warning messages

Try "ifconfig" afterwards and have a look, if the loopback device is there again. 

btw, did you encounter any other problems? I've never tried running a system without loopback, but I guess that this might cause quite a lot of trouble.

---

### Post by mach5 on 2006-03-08
thnx a lot..
but i was remaining with no option but to reinstall it and i did it.. 
well thnx for the technique..
i will sure rmr it..

yea as per the erroneous, my system was givin errors while switchin off during deconfiguring the network interfaces..

---

