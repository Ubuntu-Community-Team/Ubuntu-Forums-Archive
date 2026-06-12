---
title: "Connectivity Problems"
date: 2012-05-27
forum: General Help
---

### Post by therealdave24 on 2012-05-27
Hello,

I am new to Ubuntu but want to learn about it and use it as I've heard great things.  I am currently using a live-cd session from a boot cd and I entered all the information (ip address, netmask, gateway, and DNS servers) for a wired connection.  It says I'm connected and there are two arrows, one pointing up and one pointing down, but I can't load any websites or anything.  Are there any drivers I have to install for my modem (motorola SB5101)? 

Thanks in advance

---

### Post by mikewhatever on 2012-05-27
Are you connected directly to the medem, or is there a router in between? In either case, you shouldn't need drivers, and you also shouldn't need to manually enter IP, netmask, gateway and DNS. Just connect the cable.

---

### Post by therealdave24 on 2012-05-27
Its connected directly to the modem and it works fine when using windows, just not when I boot from the live-cd.

---

### Post by therealdave24 on 2012-05-27
Also, I tried in PuppyLinux as well and the same thing happens, namely,  it says I am connected to the internet but it can't load any pages.

---

### Post by mikewhatever on 2012-05-27
Does your ISP support static IPs? Most ISPs hand out IPs dynamically, and since you are directly connected to the modem, entering a static IP wouldn't work. Have you tried the suggestion I made above?

If it doesn't work, please post the outputs of following:

nm-tool

ping -c5 173.194.70.139 #google.com

---

### Post by therealdave24 on 2012-05-27
No, my ISP only does dynamic ips, so I guess you're right that doesn't make sense why I would have to enter things in manually.  Also, I am connected to a router but it doesn't work even when I connected directly to the modem. 

NetworkManager Tool

State: disconnected

-Device: eth0 ----------------------------------------------------------
 Type:                    Wired
 Driver:                  8139too
 State:                   disconnected
 Default:                 no
 HW Address:         00:13:D3:93:E9:C7

 Capabilities:
     Carrier Detect:  yes
     Speed:             10 Mb/s

 Wired Properties:
     Carrier:            on

and then...

connect: Network is unreachable

---

### Post by therealdave24 on 2012-05-28
I figured it out using the instructions at [http://ubuntuforums.org/showthread.php?t=1773402](http://ubuntuforums.org/showthread.php?t=1773402).

---

