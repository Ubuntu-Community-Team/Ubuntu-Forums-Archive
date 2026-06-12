---
title: "Slow internet..."
date: 2006-02-06
forum: General Help
---

### Post by Ben Stamper on 2006-02-06
My internet has been rediculously unresponsive since I moved to Ubuntu. It's connected by ethernet cable to a Linksys Wireless 802.11G router(Not using wireless, just the built in router) from a Realtek network card(RTL-8139/8139C/8139C+).  The wireless router is plugged into the standard, run of the mill router given to me by Centurytel. The actual problem seems to occur somewhere between the computer and the Centurytel router, as the computer will be loading for about 9-15 seconds before there is a response on the Centurytel router. Please help? Many thanks!

---

### Post by jpkotta on 2006-02-06
I had a slow connection when I first installed Hoary.  The problem was ipv6 was screwing things up (I can't remember exactly why, though).  Look at the output of ```
lsmod | grep ipv6
```  If it returns something, then you have the ipv6 module loaded. Try ```
sudo rmmod ipv6
``` to get rid of it.  If that fixes things, do this:```
sudo su
echo "alias ipv6 off" >> /etc/modprobe.conf
echo "alias net-pf-10 off" >> /etc/modprobe.conf # (maybe)
exit
```

---

### Post by Ben Stamper on 2006-02-06
I got a response with the first command, attempted to run "sudo rmmod ipv6", and was told that the module is in use. I tried closing down all other windows and deactivating the ethernet connection, none of which helped.

---

### Post by Jason_25 on 2006-02-06
Then (as root) add ipv6 to to /etc/hotplug/blacklist and restart if you feel it will improve your speed.  This has been loaded on all the machines I've installed ubuntu on without any problem.

---

### Post by RAOF on 2006-02-06
[QUOTE=Jason_25]Then (as root) add ipv6 to to /etc/hotplug/blacklist and restart if you feel it will improve your speed.  This has been loaded on all the machines I've installed ubuntu on without any problem.[/QUOTE]
Some routers have broken IPv6 support - when using one of these routers, Ubuntu will consistenly try IPv6 first, wait for it to timeout, and then try IPv4 (which will work).  This sort of behaviour will really slow your internet down ;)

---

### Post by Khanater on 2006-02-06
[QUOTE=Jason_25]Then (as root) add ipv6 to to /etc/hotplug/blacklist and restart if you feel it will improve your speed.  This has been loaded on all the machines I've installed ubuntu on without any problem.[/QUOTE]

Im with the same problem...i do that you say and ipv6 still in use!

---

### Post by GTvulse on 2006-02-06
[QUOTE=Khanater]Im with the same problem...i do that you say and ipv6 still in use![/QUOTE]
Add this to [font=monospace]/etc/sysctl.conf[/font]:
```

net.ipv6.conf.all.dad_transmits = 0
net.ipv6.conf.all.autoconf = 0
net.ipv6.conf.all.accept_redirects = 0
net.ipv6.conf.all.accept_ra = 0
net.ipv6.conf.all.forwarding=0 
net.ipv6.conf.all.router_solicitations=0

```

If you want to disable ipv6 in a running session, type this:
```

sudo su -
sysctl -w net.ipv6.conf.all.dad_transmits = 0
sysctl -w net.ipv6.conf.all.autoconf=0 
sysctl -w net.ipv6.conf.all.accept_ra=0 
sysctl -w net.ipv6.conf.all.accept_redirects=0 
sysctl -w net.ipv6.conf.all.forwarding=0 
sysctl -w net.ipv6.conf.all.router_solicitations=0
exit

```

---

### Post by snl on 2006-02-07
[QUOTE=Ben Stamper]I got a response with the first command, attempted to run "sudo rmmod ipv6", and was told that the module is in use. I tried closing down all other windows and deactivating the ethernet connection, none of which helped.[/QUOTE]

I had the same problem. I disable ipv6 following the instruction on this page  [https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28IPv6%29]("https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28IPv6%29")

```
   1. sudo gedit /etc/modprobe.d/aliases 
   2. Find the line:  alias net-pf-10 ipv6 
   3. Replace it with:  alias net-pf-10 off 
   4. Save the file and restart your computer

You must reboot for changes to take effect. 
```

---

### Post by Khanater on 2006-02-08
[QUOTE=snl]I had the same problem. I disable ipv6 following the instruction on this page  [https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28IPv6%29]("https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28IPv6%29")

```
   1. sudo gedit /etc/modprobe.d/aliases 
   2. Find the line:  alias net-pf-10 ipv6 
   3. Replace it with:  alias net-pf-10 off 
   4. Save the file and restart your computer

You must reboot for changes to take effect. 
```[/QUOTE]

Dont know why, but if do that changes dont have internet connection anymore.

---

