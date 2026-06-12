---
title: "Unable to hibernate computer after upgrading to Ubuntu 10.10"
date: 2010-10-20
forum: General Help
---

### Post by bkchng on 2010-10-20
Hi guys,

I've just upgraded from 10.04 to 10.10 (32 bits). Everything seemed to be working great until I tried to hibernate; now it just goes into a blank screen and the "crescent" hibernation/suspend blinking LED on my Lenovo X200 just keeps blinking, and I had to force-shutdown the computer to turn it off. In short, hibernation doesn't work for me in 10.10. This didn't happen prior to the upgrade.
Any idea how I could solve this problem? Suspend works fine though.
Thanks!

---

### Post by decrow06 on 2010-10-20
I am having the same problem.  Any ideas?  My swap space is large enough.

---

### Post by catalin.hritcu on 2010-10-21
Same problem here on two Dell laptops (Latitude E6400 and E4300) after upgrading to Ubuntu 10.10 a week ago. Most of the time hibernate just blocks with a black screen, but a couple of times it actually worked.

This is really really annoying, since first time this happened I didn't notice and put the notebook in my backpack where it stayed on for 5 hours until the battery run off. When I found it it was out of battery but still really hot :(

---

### Post by peteark on 2010-10-21
I encountered the same problem so I removed the upgrade

---

### Post by greenpeace on 2010-10-21
I'm having the same problem on this xps m1330.  Suspend works fine, and recovery is fast.  booting up and shutting down is fast.

hibernate just goes to a screen with a blinking cursor where it stays til I hard reset the laptop.

are there any bugs filed against this?  I couldn't see any

---

### Post by catalin.hritcu on 2010-10-21
Found a lot of recently submitted bugs on launchpad that could be related to our problem:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/658108](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/658108)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/658937](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/658937)
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/660405](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/660405)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/661711](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/661711)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/663575](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/663575)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/664269](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/664269)

---

### Post by InphekD on 2010-10-21
IMHO hibernation is buggy in ubuntu. But why do you need it at all? Shutdown/Startup takes just a few seconds.

---

### Post by catalin.hritcu on 2010-10-21
> **InphekD said:**
> IMHO hibernation is buggy in ubuntu. But why do you need it at all? Shutdown/Startup takes just a few seconds.

I use hibernate because I want to resume working exactly where I left off, without having to start again all applications I had started before, without having to open all documents that I had open before, without even having to remember what I was doing in the first place ;)

---

### Post by catalin.hritcu on 2010-10-21
> **InphekD said:**
> IMHO hibernation is buggy in ubuntu.

For me it worked very well until the 10.10 update.

---

### Post by catalin.hritcu on 2010-10-22
Booting with the previous kernel 2.6.32-25 (the one before the upgrade) seems to have solved the problem for me. It seems that this problem was introduced by kernel version 2.6.35-22.

---

### Post by tuxose on 2010-10-26
Same here. Dell Latitude with nVidia G86M [Quadro NVS 135M]. I suspect the nvidia driver to be the cause of this syndrome.

---

### Post by XMica on 2010-10-26
I've got the same issue after having upgraded from 10.04 to 10.10 on a Dell latitude E6410 with Nvidia nvs card.
Hibernate does not work at all (blinking cursor) and I have to power off.
Just after the upgrade to 10.10 I also faced an issue while going to standby but it has been fixed by adding "acpi_sleep=nonvs" to grub (GRUB_CMDLINE_LINUX).
However hibernate issue is still there.
Michael

---

### Post by Hack.The.Pow. on 2010-10-27
same problem here

---

### Post by Quackers on 2010-10-27
Hibernate has never worked properly for me with Lucid or Maverick. Fortunately suspend works perfectly.

---

### Post by katykat on 2010-10-27
Ditto.

Goes to sleep, but when I briefly hit the power button the monitor loses the video signal and the disk starts spinning up. 

Also with an old nvidia card. 

However: In my case at least if I press and HOLD ctrl-alt-delete for a couple minutes it WILL power down. It beats a power shutdown on a running ext4 hard drive.

---

### Post by Hack.The.Pow. on 2010-10-27
I actually just fixed it by installing a new kernal.  

I just followed the instructions in the second post in this thread.

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10031985](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10031985)

All you have to do is choose a pretty recent kernal and determine if you have an i386 architecture or amd64 by executing uname -m.(anything with an i infront of it just select i386).

Follow the instructions and you should be set.

---

### Post by netipot on 2010-10-27
My T60 had no problem with lucid when I closed the lid but after the upgrade to 10.10 it wouldn't wake up. I went into power management and changed the setting from suspend to hibernate and it has been working fine but it is not as fast as suspend was.

---

