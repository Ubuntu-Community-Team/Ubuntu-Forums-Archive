---
title: "apt-get/synaptic broken"
date: 2006-02-05
forum: General Help
---

### Post by Brando569 on 2006-02-05
i upgraded from kde 3.5 to 3.5.1 and after it was doen synaptic gave an error about avahi-daemon and i didnt know what it was and ignored it. now everytime i try to use apt-get i get this:

bran@ra:~$ sudo apt-get remove gaim
Reading package lists... Done
Building dependency tree... Done
Package gaim is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up avahi-daemon (0.5.2-1) ...
/var/lib/dpkg/info/avahi-daemon.postinst: line 29: dbus-send: command not found
dpkg: error processing avahi-daemon (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 avahi-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)

i search the forums and found other ppl were have the same problem that i was having, but not because of 3.5.1 and there werent any solutions to the problem

---

### Post by Brando569 on 2006-02-05
this is the error that synaptic gives me:

E: avahi-daemon: subprocess post-installation script returned error exit status 127

---

### Post by nrwilk on 2006-03-06
I have the exact same problem.  Every time I use apt-get I get that error.

I just uninstalled the avahi package.  Hope it's not essential!

---

### Post by Jucato on 2006-03-06
Take from apt-cache show avahi-daemon:
```
Avahi is a fully LGPL framework for Multicast DNS Service Discovery.
 It allows programs to publish and discover services and hosts
 running on a local network with no specific configuration.  For
 example you can plug into a network and instantly find printers to
 print to, files to look at and people to talk to.
 .
 This package contains the Avahi Daemon which represents your machine
 on the network and allows other applications to publish and resolve
 mDNS/DNS-SD records.
```
So I guess, unless you are running in a local network, it would be save to remove. I don't have mine installed, btw. :D

---

### Post by nrwilk on 2006-03-06
Too bad it's broken, it sounds like a very useful tool.

Probably better for the people who take laptops to multiple networks regularly.

Good thing this is a desktop box.

---

### Post by jimbren on 2006-03-07
Have you tried running apt-get with the fix flag?
 
Try this:
```
 
sudo apt-get install update
 
sudo apt-get install -f

```
 
Update is straight forward enough--updates your sources.list
 
The install -f flag will attempt to fix any broken packages and missing dependancies. 
 
This is usually one of the first things I do when I have a problem with an installation.

---

### Post by nrwilk on 2006-03-07
I had tried it.  Still had the same problem, though.

Good suggestion! :)

---

### Post by Jucato on 2006-03-07
By the way, just you should know. I did a bit of research and saw this:

[https://launchpad.net/distros/ubuntu/+source/avahi/+bug/31458]("https://launchpad.net/distros/ubuntu/+source/avahi/+bug/31458")

So if you really need avahi-daemon, you'll have to install dbus-1-utils. :D

---

### Post by nrwilk on 2006-03-10
[QUOTE=Fenyx]By the way, just you should know. I did a bit of research and saw this:

[https://launchpad.net/distros/ubuntu/+source/avahi/+bug/31458]("https://launchpad.net/distros/ubuntu/+source/avahi/+bug/31458")

So if you really need avahi-daemon, you'll have to install dbus-1-utils. :D[/QUOTE]

Perfect, Fenxy.  This fix works flawlessly.

Thank you!  :-D

---

