---
title: "Remote only works after restarting lirc"
date: 2012-03-02
forum: General Help
---

### Post by Axio on 2012-03-02
Hi,

I have configured my remote so that it works well with xbmc. However it is not yet perfect. When I boot the computer my remote doesn't work, I have to restart lirc. I don't really understand why. Here is the kernel log: [http://pastebin.com/Tua3XXD8](http://pastebin.com/Tua3XXD8)

I don't understand why at boot it fails to find the remote. What should I do?

---

### Post by aeiah on 2012-03-02
presumably the first time, when it fails, something which lirc relies upon hasn't happened yet. you could make lirc start later in your boot sequence. it fails on 
```

unable to find 'name=IR*'

```

looks like it pulls this from a config file - perhaps you can find more information on it there? 'name=IR*' tends to suggest its a rather generic infared receiver.

you could also go the lazy way and see if adding 
```

sudo /etc/init.d/lirc restart

```
to /etc/rc.local fixes it, but its a bit dirty.

---

### Post by Axio on 2012-03-02
Thanks for your answer. I tried the "lazy way", but it didn't work. Also I noticed something, if after the boot I restart lirc with ssh the hardware is recognised (if I believe syslog) but my remote still doesn't work. It seems that I have to restart lirc in a terminal from the desktop.

> 
----
boot
----
Mar  2 14:11:02 xavier-server kernel: [   14.902841] lirc_dev: IR Remote Control driver registered, major 248 
Mar  2 14:11:02 xavier-server lircd-0.9.0[1095]: lircd(devinput) ready, using /var/run/lirc/lircd
Mar  2 14:11:02 xavier-server lircd-0.9.0[1095]: accepted new client on /var/run/lirc/lircd
Mar  2 14:11:02 xavier-server lircd-0.9.0[1095]: initializing 'name=IR*'
Mar  2 14:11:02 xavier-server inputlircd: Started
Mar  2 14:11:03 xavier-server lircd-0.9.0[1095]: unable to find 'name=IR*'
Mar  2 14:11:03 xavier-server lircd-0.9.0[1095]: Failed to initialize hardware
Mar  2 14:11:27 xavier-server lircd-0.9.0[1095]: you are using an obsolete devinput config file: Inappropriate ioctl for device 
Mar  2 14:11:27 xavier-server lircd-0.9.0[1095]: get the new version at [http://lirc.sourceforge.net/remotes/devinput/lircd.conf.devinput:](http://lirc.sourceforge.net/remotes/devinput/lircd.conf.devinput:) Inappropriate ioctl for device
------
restart from ssh
------ 
Mar  2 14:12:03 xavier-server lircd-0.9.0[1095]: removed client
Mar  2 14:12:03 xavier-server lircd-0.9.0[1095]: closing '/dev/input/event7'
Mar  2 14:12:03 xavier-server lircd-0.9.0[1095]: caught signal
Mar  2 14:12:03 xavier-server lircd-0.9.0[2274]: lircd(devinput) ready, using /var/run/lirc/lircd
Mar  2 14:12:03 xavier-server lircd-0.9.0[2274]: accepted new client on /var/run/lirc/lircd
Mar  2 14:12:03 xavier-server lircd-0.9.0[2274]: initializing 'name=IR*'
Mar  2 14:12:05 xavier-server lircd-0.9.0[2274]: you are using an obsolete devinput config file: Success 
Mar  2 14:12:05 xavier-server lircd-0.9.0[2274]: get the new version at [http://lirc.sourceforge.net/remotes/devinput/lircd.conf.devinput:](http://lirc.sourceforge.net/remotes/devinput/lircd.conf.devinput:) Success 
------
restart from desktop
------
Mar  2 14:13:17 xavier-server lircd-0.9.0[2274]: removed client
Mar  2 14:13:17 xavier-server lircd-0.9.0[2274]: closing '/dev/input/event7'
Mar  2 14:13:17 xavier-server lircd-0.9.0[2274]: caught signal
Mar  2 14:13:17 xavier-server lircd-0.9.0[2416]: lircd(devinput) ready, using /var/run/lirc/lircd
Mar  2 14:13:17 xavier-server lircd-0.9.0[2416]: accepted new client on /var/run/lirc/lircd
Mar  2 14:13:17 xavier-server lircd-0.9.0[2416]: initializing 'name=IR*'
Mar  2 14:13:19 xavier-server lircd-0.9.0[2416]: you are using an obsolete devinput config file: Success 
Mar  2 14:13:19 xavier-server lircd-0.9.0[2416]: get the new version at [http://lirc.sourceforge.net/remotes/devinput/lircd.conf.devinput:](http://lirc.sourceforge.net/remotes/devinput/lircd.conf.devinput:) Success 
Mar  2 14:13:23 xavier-server lircd-0.9.0[2416]: accepted new client on /var/run/lirc/lircd

About "name=IR*", I have had a lot of problems to make lirc work correctly with xbmc and I ended up with that name, but I don't really know why.

Here is my hardware.conf for lirc:
> 
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="devinput"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="IR*"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

---

### Post by Axio on 2012-03-09
I have maybe made some progress. I played with the runlevels, by starting lirc later I manage to get this at boot:
> xavier@xavier-server:~$ cat /var/log/syslog | grep lirc
Mar  9 12:31:04 xavier-server inputlircd: Started
Mar  9 12:31:04 xavier-server kernel: [   14.506226] lirc_dev: IR Remote Control driver registered, major 248 
Mar  9 12:31:13 xavier-server lircd-0.9.0[1766]: lircd(devinput) ready, using /var/run/lirc/lircd
Mar  9 12:31:13 xavier-server lircd-0.9.0[1766]: accepted new client on /var/run/lirc/lircd
Mar  9 12:31:13 xavier-server lircd-0.9.0[1766]: initializing 'name=IR*'
Mar  9 12:31:31 xavier-server lircd-0.9.0[1766]: you are using an obsolete devinput config file: Success 
Mar  9 12:31:31 xavier-server lircd-0.9.0[1766]: get the new version at [http://lirc.sourceforge.net/remotes/devinput/lircd.conf.devinput:](http://lirc.sourceforge.net/remotes/devinput/lircd.conf.devinput:) Success

So now it initializes the remote at boot, but the remote still doesn't work. I still have to restart lirc from the desktop. Restarting from ssh for example doesn't work, it gives a similar output.

When I restart from the desktop I get this:
> Mar  9 12:32:45 xavier-server lircd-0.9.0[1766]: removed client
Mar  9 12:32:45 xavier-server lircd-0.9.0[1766]: closing '/dev/input/event7'
Mar  9 12:32:45 xavier-server lircd-0.9.0[1766]: caught signal
Mar  9 12:32:45 xavier-server lircd-0.9.0[2241]: lircd(devinput) ready, using /var/run/lirc/lircd
Mar  9 12:32:45 xavier-server lircd-0.9.0[2241]: accepted new client on /var/run/lirc/lircd
Mar  9 12:32:45 xavier-server lircd-0.9.0[2241]: initializing 'name=IR*'
Mar  9 12:32:55 xavier-server lircd-0.9.0[2241]: you are using an obsolete devinput config file: Success 
Mar  9 12:32:55 xavier-server lircd-0.9.0[2241]: get the new version at [http://lirc.sourceforge.net/remotes/devinput/lircd.conf.devinput:](http://lirc.sourceforge.net/remotes/devinput/lircd.conf.devinput:) Success 
Mar  9 12:32:59 xavier-server lircd-0.9.0[2241]: accepted new client on /var/run/lirc/lircd

The main difference is that when I restart from the desktop I get this message: "lircd-0.9.0[2241]: accepted new client on /var/run/lirc/lircd"

How come when I restart lirc from ssh or when I boot, it is not accepted on /var/run/lirc/lircd?

---

### Post by Axio on 2012-03-13
I didn't find a proper solution, so I just put this script at startup:
```
#!/bin/bash

sudo /etc/init.d/lirc restart
read -p "Password: " XXXXXXXXX
```

It is ugly and dirty, but it works!

---

