---
title: "Xorg using 90% of CPU"
date: 2010-04-15
forum: General Help
---

### Post by Felix_the_Mac on 2010-04-15
Hi,

we suffered a brief (10 second) power cut this morning leading to a hard power off.
Since that time, when I log in to Gnome, my system is very slow to respond. System monitor shows constant CPU activity even when I am doing nothing.
top command reports that Xorg is using ~90% of CPU.

I have forced an fsck on all drives and rebooted multiple times to no effect.

Can anyone please suggest steps to troubleshoot/resolve?

Thanks

System details:
Linux molly 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux
Quad core Opteron 1352 2.1GHz
4GB RAM
Seperate partitions for / /home /boot /tmp
plenty of disk space.

---

### Post by Felix_the_Mac on 2010-04-15
I have removed the proprietary ATI driver and am using the kernel driver. CPU usage now 60% instead of 90%.

Any ideas? Thanks

---

### Post by Felix_the_Mac on 2010-04-19
I have upgraded to 10.04, but the problem persists.
Any ideas anyone?

Thanks

Linux molly 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux

---

### Post by linden940 on 2010-04-19
wow...not even sure what to say or think on this one...only thing i can think is rebooting but you said that you tryed that...did you go into a older kernel and see if that fixed it?

maybe the kernel is messed up and a reformat may need to be done but before doing that I'll go into a older kernel and see if you JUST reinstall the most-up-to-date kernel again if it would fix it or not

---

### Post by klemes on 2010-04-19
I do not have a hint for your problem,but since you took the step to upgrade to 10.4 a clean installation would be much preferable since you say you have a seperate /home partition.
If you do it this way just choose not to format your home partition in the initial faces of the installation procedure just choose this particular partition and choose /home as your mountpoint leaving unchecked the format button and providing the correct filesystem type where it's required.

---

### Post by Felix_the_Mac on 2010-04-19
Klemes, 

thanks, that is  a pretty good suggestion.
However I am nervous of doing that because this is my file server with software based raid array and I have no means of backing it up.

Basically, doing a fresh install is to scary!

Thanks

---

### Post by klemes on 2010-04-19
Maybe another option would be to try use any old  video card lying around or a friend's exchange card to see if the power cut did any damage to your current video card?

---

### Post by Felix_the_Mac on 2010-04-19
thanks, thats another good idea. I may try that later.

At the moment I am hoping to debug the current issue, by looking at log files etc and hopefully working out what Xorg thinks it is doing. To that end I have posted a query to the Xorg mailing list and with luck will get some expert replies.

Thanks

---

### Post by iponeverything on 2010-04-19
For debugging:

Look at the xorg log file in /var/log (also look at messages, syslog and debug)

use lsof on the X process to see what it is accessing

and use strace to attach to running x process to see what it is chewing on. Do ctrl-c to stop the trace.

---

### Post by Owen.C93 on 2010-04-25
I also have this problem. I'm using 10.04 so will start a new thread over there later. I can't figure out if it's firefox related or usb drive.

---

### Post by Felix_the_Mac on 2010-04-26
My issue seems to be related to VirtualBox.

I had a virtual machine that was starting automatically at boot.

With that running I could kill X and when it restarted it would still be using 90%cpu.

However if I stop the VirtualBox instance and then restart X it works properly.

---

