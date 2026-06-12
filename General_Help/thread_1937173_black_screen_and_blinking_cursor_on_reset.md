---
title: "black screen and blinking cursor on reset"
date: 2012-03-07
forum: General Help
---

### Post by Nomad5150 on 2012-03-07
I've reasearched this a lot and have tried many things. I just believe I might be doing it wrong. I installed ubuntu 11.10 from the cd and chose the option to wipe out windows. When it was all finished and asked me to restart, it started back up with just a black screen and a flashing cursor in the top left corner. What I've tried to do to fix this is mount the system from the cd and install updates. Change the boot sequence from the main disk menu. Find the GRUB to update it, but when I type the command to find it, it can't locate it, so I can't update it. 

I just think the processes I went through to fix it, I did improperly. I just need some guidance. Thanks.

---

### Post by Nomad5150 on 2012-03-07
Maybe if I loaded 10.10 it would work.

---

### Post by Nomad5150 on 2012-03-07
Anyone? Please?

---

### Post by swright007 on 2012-03-07
You mentioned that there is a blinking cursor in the upper left of the screen, I believe.    Does it ever boot to the desktop or is it just stuck there with the blinking cursor?

Scott

---

### Post by Nomad5150 on 2012-03-07
It doesn't boot to desktop. Actually it desn't boot at all really. It happens right after the splash screen that tells me I can press escape to enter boot sequence and such.

---

### Post by swright007 on 2012-03-08
first thing I would do would be to boot from a live CD and update the grub. 

open a terminal and issue the command :

sudo update-grub

---

### Post by Nomad5150 on 2012-03-08
Ok. Ill try that when I get home from work. Thanks.

---

### Post by Nomad5150 on 2012-03-09
Didn't work.

---

### Post by Jakob45 on 2012-03-09
Out of interest this sounds like the same issue I am having (only i'm dual booting with windows) if you press and hold shift on start up do you get a line of text which reads

GRUB Loading.
_

This link may help you out I havn't tried it yet
[http://ubuntuforums.org/showthread.php?t=1313207](http://ubuntuforums.org/showthread.php?t=1313207)

(The code you may find helpful is
sudo dpkg-reconfigure grub-pc but read the thread and see what you think)

(Also you may want to look into editing the file ect/default/grub)

Would appreciate a heads up if it works

---

### Post by gordintoronto on 2012-03-09
Can you tell us exactly what options you took during installation?

I've never just taken defaults during installation, so I don't know how it sets up the hard drive. I have always manually partitioned the drive, with, for example, a small (200 MB?) boot partition, and an extended partition containing a / (root) partition of perhaps 20 GB, a swap partition which is a bit larger than main memory, and the rest as /home. Then I tell it to put Grub in the boot partition.

"sudo update-grub" from the CD won't ever do anything useful.

I've never seen a message which looked like, "I can press escape to enter boot sequence and such." If you lean on the shift key during boot-up, do you see a Grub menu?

---

