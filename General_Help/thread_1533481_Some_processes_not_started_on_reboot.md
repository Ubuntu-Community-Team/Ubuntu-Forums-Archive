---
title: "Some processes not started on reboot"
date: 2010-07-18
forum: General Help
---

### Post by georgesgiralt on 2010-07-18
Hello !
I've a laptop running 10.04 LTS 64 bit. (Upgraded from 9.04 64bit).
Some times (1 over 3) certain processes are not started at boot time : bluetooth, vboxdrv, hddtemp, cups.... (I may miss some other ones).
If I use sudo and the service command I can start them by hand and if I reboot they usually start automatically.
I've tried to start the laptop without the "quiet splash" options to the kernel command line but I did not see any error messages nor anything more explaining this behavior. 
So I wonder where I can find where the glitch is, how I can fix it, and what is the startup sequence of an Ubuntu machine (there is no /etc/inittab, and the /etc/rcN behavior does not seem to be standard)
Many thanks in advance for your answer and help.

---

### Post by dino99 on 2010-07-18
some basic control:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

to hunt errors, look at .xsession-errors (/home, ctrl+h to unhide) and into : system admin logviewer

---

### Post by georgesgiralt on 2010-07-24
Hello Dino99 !
I've done further investigations.
First I ran all the commands you specified and they found a couple of unused packages to remove. But this did not solve my problem.
On the various log files I looked at, all I can say is that on boot.log there is no further messages after the filesystem clear one from fsck. So debugging will be harsh... 
I am very familiar with vanilla Unix systems so I began to look at the various startup script I know off and found no inittab defining the run level init will use. So could you point me toa documentation describing the Ubuntu boot process and the variables associated with ? 
Many thanks in advance for your help.
Regards

---

### Post by 10027586 on 2010-08-07
I've run into much the same problem and as yet found no obvious solution. It does seem as if there's a problem at the init end of things.

---

### Post by 10027586 on 2010-08-07
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554172](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554172) for the bug in Launchpad, seems to correlate to what we're experiencing (and I've had it on multiple installs).

One temp solution suggested in the bug thread is to reinstall CUPS. Gonna give it a try and report back on any success/failure (though the intermittent nature of the fault makes it hard to tell if the problem is solved or not).

---

