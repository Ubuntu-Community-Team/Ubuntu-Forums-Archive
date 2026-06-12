---
title: "Connection Problems"
date: 2011-06-18
forum: General Help
---

### Post by Maverick Mungbean on 2011-06-18
Hey Guys, 
I´m running Natty on my Lenovo g550 and my wireless works fine when I am at home, but I am at a friends house right now and I am trying to get in his Wireless (which is not locked or anything.)
**So the first thing we did** of course is click on the Wireless (I would love to show you pictures but <i cant get it to his laptop, from which I am writing this now.)
It searched around for it about 30 seconds and then told me "Wireless Network: Disconnected, you are now offline."
**The Second thing we tried was **a simple ethernet connection which then also did not work. 
 
The Wireless router is a Netgear .
 
So we/I am in a bit of a pickle right now. I would appreciate a quick answer .
 
If you have any questions please ask me in this topic, I will be monitoring it for the rest of the day.
 
Regards, 
William

---

### Post by SACHINVD on 2011-06-18
To setup broadband connection you can use command
```
sudo pppoeconf
```

don't know about wireless.

---

### Post by Maverick Mungbean on 2011-06-18
> **SACHINVD said:**
> To setup broadband connection you can use command
```
sudo pppoeconf
```
 
don't know about wireless.
 Thanks but it didnt work, it searched for the pppoe things but apparently the access concentrator didnt respond. But all my cables are in the right place (it only has one cable, the ethernet cable.)

---

### Post by SACHINVD on 2011-06-18
Can you post output of 
```
ifconfig
```

and you can whether you have Ethernet controller or not by using command 

```
lspci | grep Ethernet
```

see if above command gives any output or not ?

---

### Post by Maverick Mungbean on 2011-06-18
> **SACHINVD said:**
> Can you post output of 
```
ifconfig
```
 
and you can whether you have Ethernet controller or not by using command 
 
```
lspci | grep Ethernet
```
 
see if above command gives any output or not ?
 
I cant give you the output because i cant upload it from the ubuntu i am running on the device which isnt connecting me to the internet. the first one gives me 3 paragraphs and it doesnt work...to upload..
 
The second says 
 
07:00.0 [COLOR=red]Ethernet[/COLOR] controller: Broadcom Corporation Netlink BCM5906 Fast [COLOR=red]Ethernet[/COLOR] 
PCI Express (rev 02)

---

### Post by SACHINVD on 2011-06-18
Output of commands indicates you have ethernate driver in place.

There is one more way to setup connection

Goto System->Preferences->Network Connection

and If you have braodband connection then select DSL tab
and enter username and password of broadband

and if you have wired connection then you need to provide IP address and DSN.

---

### Post by Maverick Mungbean on 2011-06-18
> **SACHINVD said:**
> Output of commands indicates you have ethernate driver in place.
 
There is one more way to setup connection
 
Goto System->Preferences->Network Connection
 
and If you have braodband connection then select DSL tab
and enter username and password of broadband
 
and if you have wired connection then you need to provide IP address and DSN.
The problem is with wireless, its got neither a username nor a password, it s an open connection but th elaptop wont connect to it! And its the same with the wired connection
 
Look, if I edit the wired connection it gives me a MAC Address . And when <i hover over it it says "this option Locks this connection to the network device specified by its permanent MAC address entered here." Maybe that could be a solution? What wqould i have to tipe in there then? And what the hell is the cloned mac adress?°

---

### Post by SACHINVD on 2011-06-18
If its problem of Wireless then you need to see about "Broadcom drivers".
They are by default after Ubuntu 10.10.
There might be issue with broadcom drivers.

I don't know much about troubleshooting it but you can get search it on forums you will get solution.

---

### Post by Maverick Mungbean on 2011-06-18
> **SACHINVD said:**
> If its problem of Wireless then you need to see about "Broadcom drivers".
They are by default after Ubuntu 10.10.
There might be issue with broadcom drivers.
 
I don't know much about troubleshooting it but you can get search it on forums you will get solution.
 
 
ok . I got the ethernet working, it says I am connected but I cant open any pages!

---

### Post by SACHINVD on 2011-06-19
You can try one thing then

Open /etc/resolve.conf in gedit or vi

Add google dsn to file , save it and close then check whether pages are opening or not

You can add following lines to /etc/resolv.conf

nameserver 8.8.8.8
nameserver 8.8.4.4

---

