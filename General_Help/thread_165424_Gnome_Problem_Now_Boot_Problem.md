---
title: "Gnome Problem Now Boot Problem???"
date: 2006-04-24
forum: General Help
---

### Post by GoJimbo on 2006-04-24
I was using the terminal when I got a Gnome Application Error, it quit unexpectedly and I've been unable to use it since.  

Also tried to re-install Gnome with my Hoary disc but the server is not recognizing the drive.  

Tried going to users and groups in sysadmin but password not accepted.

Tried to reboot and now I'm getting the following:

[B]Uncompressing Linux.... Ok, booting the kernel.

PCI: Cannot allocate resource region 4 of device 0000:00:07:1
audit (1145902873.133:0): initialized
Starting Ubuntu...
* cannot execute "/etc/init.d/rcS"
* Entering runlevel: 2
* cannot execute "etc/init.d/rc"

Ubuntu 5.04 "Hoary Hedgehog " (none) tty1

(none) login: [/B]

Not accepting my login at the prompt.  Running on an Dell PowerEdge 2300.  

Help please.

Jim

---

### Post by GoJimbo on 2006-04-24
Think it was just a case of newbie stupidity. 

After numerous reboots and failed attempts to access via single-user my cd drive was finally recognized and I ran rescue with my install disc.  It worked fine until the end when it told me my /bin/bash/ directory was gone, no shell, no command line...

I was working through a tutorial on creating bash scripts when I had the problem with gnome terminal.  

Luckily I have a back-up machine.

Will see what else I can break tomorrow.

---

