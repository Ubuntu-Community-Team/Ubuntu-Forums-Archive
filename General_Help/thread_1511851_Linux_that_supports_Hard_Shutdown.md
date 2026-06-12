---
title: "Linux that supports Hard Shutdown"
date: 2010-06-17
forum: General Help
---

### Post by rcacheira on 2010-06-17
hello guys, 
I'm new here but I really need some help here, I'm making a machine with  no keyboard or mouse support for users, so I need the machine to  support "hard shutdown" without spoiling the initialization files of  Linux
 
The machine has 1GB of disk, and the processor can be between (200 to  500Mhz), and linux version must support incoming ssh connections and  local network.
 
I'm using puppy linux, but it is a very heavy and on the "Hard Shutdown"  is a disaster.
 
Someone can help me?

---

### Post by bobcollard on 2010-06-17
> **rcacheira said:**
> The machine has 1GB of disk, and the processor can be between (200 to 500Mhz), and linux version must  support incoming ssh connections and local network.

I'm using puppy linux, but it is a very heavy and on the "Hard Shutdown" is a disaster.

Someone can help me?
Try Linux Mint 8 Fluxbox.  It is light, fast and should be able to handle it.

---

### Post by tgalati4 on 2010-06-17
You want to run in RAM.  Try tinycore.

---

### Post by rcacheira on 2010-06-17
Sorry but, [I] forgot to put the first line!!!
[/I]

---

### Post by _Mark_ on 2010-06-17
OK whats a hard shutdown?

To be honest you won't find much lighter than Puppy have used it on various old laptops and desktops and never had a problem with shutdown, hard or otherwise

---

### Post by rcacheira on 2010-06-17
Hard Shutdown is Powerdown without shutdown command, or unplug de energy cable

---

### Post by bodhi.zazen on 2010-06-17
> **rcacheira said:**
> hello guys, 
I'm new here but I really need some help here, I'm making a machine with  no keyboard or mouse support for users, so I need the machine to  support "hard shutdown" without spoiling the initialization files of  Linux
 
The machine has 1GB of disk, and the processor can be between (200 to  500Mhz), and linux version must support incoming ssh connections and  local network.
 
I'm using puppy linux, but it is a very heavy and on the "Hard Shutdown"  is a disaster.
 
Someone can help me?

such "hard shutdowns" as you are calling them should be avoided with any OS.

I suggest you install ssh (server) and issue a shutdown command via ssh

ssh user@server shutdown -h now

---

### Post by _Mark_ on 2010-06-17
> **rcacheira said:**
> Hard Shutdown is Powerdown without shutdown command, or unplug de energy cable

Would have to agree with bodhi.zazen you are asking for trouble doing that. no wonder you have puppy problems

---

### Post by rcacheira on 2010-06-17
I know that, so what i  need is something like DOS but Linuxnao need a graphical interface,  just need the console to launch processes compiled in C + +, also need  to ssh to change configuration parameters and to download files from the  machine. Technicians also will not have  access to the mouse and keyboard but will need to turn off the machine  by the button with two positions on / off

---

### Post by bodhi.zazen on 2010-06-17
> **rcacheira said:**
> I know that, so what i  need is something like DOS but Linuxnao need a graphical interface,  just need the console to launch processes compiled in C + +, also need  to ssh to change configuration parameters and to download files from the  machine. Technicians also will not have  access to the mouse and keyboard but will need to turn off the machine  by the button with two positions on / off

Sounds as if you already have ssh installed, why not use it ?

You can configue ssh keys to use forced commands if need be.

Turning the machine off via the power button is just begging for problems.

---

### Post by rcacheira on 2010-06-18
Because  the technicians will not have access to ssh. and  the only button you will have access is the power button on / off

---

### Post by bobcollard on 2010-06-18
> **rcacheira said:**
> Because  the technicians will not have access to ssh. and  the only button you will have access is the power button on / off
Well, I've been following this thread to see how it would turn out.  I have to agree that cutting the power on purpose is not a good thing.  My original recommendation for Linux Mint Fluxbox was because we have power outages during storms that have been recoverable on my computer with fluxbox.  This sounds like a headless server, but, why a technician would need to turn it off often is beyond me.

---

### Post by MooPi on 2010-06-18
You can use Ubuntu for this purpose. I'm using the Gnome desktop on my computer and if I hit the power button on my computer a dialog windows pops up and gives the choice for "shutdown" "restart" "hibernate". The first choice being shutdown will occur 1 minute later if no other action is taken. The OS will do a proper shutdown for you.

---

### Post by dcstar on 2010-06-18
> **MooPi said:**
> You can use Ubuntu for this purpose. I'm using the Gnome desktop on my computer and if I hit the power button on my computer a dialog windows pops up and gives the choice for "shutdown" "restart" "hibernate". The first choice being shutdown will occur 1 minute later if no other action is taken. The OS will do a proper shutdown for you.

Another option is to install a pseudo-Live CD/USB system that has most OS stuff running in RAM and only access the data disks for RW stuff.

You would want to run the data disks without any write caching whatsoever and hope that the journaling of whatever FS you use will make it resilient enough to withstand something as stupid as power-offs without proper shutdowns.

---

### Post by bodhi.zazen on 2010-06-18
> **rcacheira said:**
> Because  the technicians will not have access to ssh. and  the only button you will have access is the power button on / off

It is trivial to give the techs ssh access.

---

### Post by iponeverything on 2010-06-18
If the system does not need dynamic data, just have it like ground hog day. Two data partitions, on boot the static partition is copied over to the disposable one and then chroot'ed.

---

### Post by jerome1232 on 2010-06-18
Isn't there a program called apicd (or something like that) That will initiate a proper shutdown if it picks up that the power button was pressed? (that's assuming this is a regular pc power button, not a true on/off switch)

---

### Post by bobcollard on 2010-06-18
Put Puppy on a Thumb Drive, Boot up and run it on the computer's RAM.  Let them shut it down and see if it hurts the thumb drive.

---

### Post by Linuxforall on 2010-06-18
Ubuntu allows safe shutdown via power button, just configure it in power management.

---

