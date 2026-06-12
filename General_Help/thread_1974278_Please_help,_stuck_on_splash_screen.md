---
title: "Please help, stuck on splash screen"
date: 2012-05-05
forum: General Help
---

### Post by Musicmaker384 on 2012-05-05
Just install Ubuntu 12.04 LTS from a Live CD. 

I can select [Ubuntu, with Linux] from the Grub menu, and it will start to boot, but it'll just hang on the splash screen (the Ubuntu logo and the five orange dots animation).

This was a brand-new install - I haven't had any previous releases of Ubuntu on this PC.

Already searched the web extensively, nothing looks like it'll do the trick.

Help would be appreciated.

EDIT: I have left it this way for well over 20 minutes. I don't think any OS in existence takes that long to start.

---

### Post by wilee-nilee on 2012-05-05
You can hit the up arrow I believe to see the text and see where it stops and let us know. You might check the md5sum as well.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Musicmaker384 on 2012-05-05
Alright, I'll do that. Should take just a a few minutes.

---

### Post by pqwoerituytrueiwoq on 2012-05-05
this could be a issue with a driver and lightdm
you can switch to gdm
ctrl+alt+f1 should get you to a tty login if not you cna boot to recovery mode
```
sudo apt-get purge lightdm;sudo apt-get install gdm
```
gdm is not as pretty or have a on screen keyboard for login but it does work

---

### Post by Musicmaker384 on 2012-05-05
I pressed the up arrow key and saw all the processes loading.

Here's what it gave me, to the best of my knowledge:

fsck from util-linux 2.20.1
/dev/sda5 was not cleanly unmounted, check forced.
/dev/sda5: 179986/21626880 files (0.1% non-contiguous)
mountall: fsck / [412] terminated with status
 * Starting mDNS/DNS-SD daemon
modem-manager [564]: <info> ModemManager (version was here, can't remember what it was)

It then loaded about 10 plugins, all of which went off without a hitch.

Came to:

 * Starting bluetooth daemon [OK]
 * Starting configure network device security [OK]
 * Starting network connection manager [OK]
 * Starting CUPS printing spooler/server [OK]

And it stopped there. I'm quite sure that's as far as it will go.

I can boot into recovery mode just fine, I was actually just running memory tests not too long ago.

It may help to know that I had a problem installing a bootloader. To be honest, I'm new at this and I'm not quite sure what that is. It is the Grub menu, correct? I entered a few commands from a Terminal in the Live CD instance and manually installed it. I think so, anyway. If this is the problem, please forgive my stupidity.

I should also note that I installed Ubuntu on a separate partition from C:/, away from Windows.
When I use Disk Management on Windows, it tells me that dev/sda5, the partition I installed Ubuntu on, is 100% free. Is that normal...?

---

### Post by pqwoerituytrueiwoq on 2012-05-05
since windows does not know what a ext4 partition even is much less what is in it, so yes it is normal
if i were you i would just give gdm a try see previous post
to undo it you simply switch gdm with lightdm in the command

---

### Post by Musicmaker384 on 2012-05-05
I'll give it a try.

---

### Post by Musicmaker384 on 2012-05-05
You probably won't believe this, but I pressed CTRL+ALT+F1, but I was given no login interface, just a blinking cursor. I took it that this might take a while, so I left it alone for a few minutes. Nothing happened. It's hanging on the cursor.

I pressed CTRL+ALT+DEL, and got an few error message. It was only onscreen for about a second:

"Cannot get (or maybe it was start)...please make sure" is all I remember.

I am curious about having Ubuntu alongside Windows on the same partition. If I delete the ext4 partition using Disk Management, nothing on my Windows partition will be harmed, correct? I don't want to give up having Ubuntu on its own partition, I just want to know as a last resort.

---

### Post by Musicmaker384 on 2012-05-06
Bump.

If this thread is dead, I'll delete the partition and recreate it, and attempt a fresh installation.

---

### Post by Harry.k on 2012-05-06
I had bootup trouble with precise too. What is your hardware? If the gpu is intel, g may have a solution

---

### Post by Musicmaker384 on 2012-05-06
Well, to be honest, I actually have an AMD. 

But actually, I just performed a reinstallation through the Live CD, and when I did it the Grub menu looked different. I think the problem was caused by me manually installing an old version of Grub. I can't be certain, but that's what I think. Anyway, thanks for offering, everything's fixed now.

I'm marking this thread as solved.

---

