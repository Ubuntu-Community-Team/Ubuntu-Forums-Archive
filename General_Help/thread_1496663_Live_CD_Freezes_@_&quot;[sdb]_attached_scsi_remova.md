---
title: "Live CD Freezes @ &quot;[sdb] attached scsi removable disk&quot;"
date: 2010-05-29
forum: General Help
---

### Post by cpl_usmc on 2010-05-29
Trying to boot Ubuntu live CD 10.04 and getting some problems.  I will get to the section where I have to pick a language and then choose the option to run from the CD.  It will start to load and then it will hang up at **"[sdb] attached scsi removable disk"**.  I unplugged all of my external HD's.  I burned the 32 bit version because it was recommended on the site.

Asus
Pentium Dual core CPU E5400 @ 2.70 GHz
5 Gigs of RAM
Current clock speed 2700MHz
Running Windows 7 

Any Ideas will be appreciated!!!

---

### Post by jarviser on 2010-05-29
I had a similar SCSI drive message trying to boot the latest GParted that I burned to CD stock that my PC didn't like.  I burned the ISO to DVD instead and it booted OK. Try another burn, maybe to DVD.

---

### Post by cpl_usmc on 2010-05-29
Thank you for your response, I really do appreciate any and all help.  I did burn it to a DVD, I accidentally typed CD.  I will try to burn it again and see if that works.  I am also going to try another distro of linux to see if it is a hardware incompatibility issue or a ubuntu issue.  It is a little disappointing though I wanted to try 10.04 I heard it was good.  I have been away from Ubuntu for a few years.  Again thank you.

---

### Post by jarviser on 2010-05-30
Try a different manufacture. If it's +R try -R or vice-versa. I always buy mine ready burned from a specialist (in the UK that's linux-man.co.uk)

5 GB RAM? - sounds like you may need the 64bit OS to use it all.

---

### Post by mpec on 2010-07-30
Did changing to a different CD type help in your case?

I'm experiencing the same problem with Ubuntu 10.04. However, it does not make a difference if I use a CD or bootable USB stick, I'm always stuck at the "[sdb] attached scsi removable disk" lines.


I also tried, unsuccessfully, the Ubuntu 9.10 and 9.04 Live CDs:


For 9.10 I get the following lines: 

> W: Skipping non-exisiting file /cdrom/dists/karmic/main/binary-i386/Packages
W: Skipping non-exisiting file /cdrom/dists/karmic/restricted/binary-i386/Packages
Removing any system startup links for /etc/init.d/apparmor ...

...finally there is a prompt "ubuntu@ubuntu" and after some minutes something seems to be happening, but then the screen goes black and that's it. 


And also no luck with 9.04: although I can get to the Desktop and start the installation it stops very soon with an error saying there is a problem either with the CD, the CD drive or the harddisk.


I'm not an expert at all and was hoping that someone might be able to point me to what the problem might be. 

Since it is the same with CD and USB stick, I didn't think it could be CD or CD drive. The computer was brandnew, I only installed Win7 in order to see if it would install, which it did without problem. It's got an intel core i5, 4GB and ASRock H55DE3 board (DDR2600+, Dual Channel).  (sorry if that info is incomplete, you'll notice that I really do not know a thing about computer hardware)

---

### Post by mpec on 2010-07-30
Installing 9.04 from USB stick worked!

Starting the upgrades now ..

---

