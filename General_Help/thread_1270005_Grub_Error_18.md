---
title: "Grub Error 18"
date: 2009-09-19
forum: General Help
---

### Post by BigD77 on 2009-09-19
Hi,

   I just installed Ubuntu on my P4 Dell laptop, and after the reboot I get GRUB loading, please wait...
Error 18

   I am trying to do a dual boot with Windows XP.  I never had any problems on a previous laptop that I had Ubuntu on.  Windows won't load, nothing.  What do I do now?  :confused:

---

### Post by undecim on 2009-09-19
Grub error 18 happens when GRUB tries to access data that is beyond what the BIOS can handle during boot.

You can fix this by installing Ubuntu with a small (64 MB is plenty) partition with mount point "/boot" at the beginning of your hard drive. (You will need to select the manual partition setup to do so.)

---

### Post by BigD77 on 2009-09-19
> **undecim said:**
> Grub error 18 happens when GRUB tries to access data that is beyond what the BIOS can handle during boot.

You can fix this by installing Ubuntu with a small (64 MB is plenty) partition with mount point "/boot" at the beginning of your hard drive. (You will need to select the manual partition setup to do so.)

How do you do that?  I don't want to format the entire drive, and because of two failed attempts at installing Ubuntu, the Windows portion of the drive is shrunk to 98 GB.  The drive is a 250 GB drive.  The rest is now unallocated free space.

---

### Post by Bucky Ball on 2009-09-19
This might help:

[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)

---

### Post by Roasted on 2009-09-19
Although this may be unlikely, I used to get weird boot errors with my PC and they continually got worse. I'm dual booting Vista Ultimate 32 bit + Ubuntu Jaunty 64 bit with partitions like so:

80gb NTFS - Vista
1gb SWAP - Linux
20gb ROOT - Linux
360gb HOME - Linux

Ultimately my errors got worse and worse, ranging from Error 18, 21, 16, etc. Soon every 5 times I'd reboot, it'd fail 4 times. Turned out to be a bad SATA cable.

Just something to keep in mind. Not sure if it pertains to you but I figured I'd voice my experience.

---

### Post by BigD77 on 2009-09-19
> **undecim said:**
> Grub error 18 happens when GRUB tries to access data that is beyond what the BIOS can handle during boot.

You can fix this by installing Ubuntu with a small (64 MB is plenty) partition with mount point "/boot" at the beginning of your hard drive. (You will need to select the manual partition setup to do so.)

Ok, that makes sense!  I didn't think to check the BIOS since I first loaded Windows XP, and XP showed the full 250 GB hard drive.  I checked the BIOS now and it only shows 137 GB.  

So now I am loading Ubuntu again and am leaving 100 GB for Windows.  It worked!

The first time I tried it since loading, I had NO graphics, just a blank screen.  So I re-booted into recovery mode, and that seemed to remedy it.

Life is better now.  THANKS!!!!   :P

---

### Post by BigD77 on 2009-09-19
And also, (Since this is an older laptop without a built in WiFi card), the NEC Warpstar Aterm WL54AG Triple Wireless Lan Card worked flawlessly with no additional work.  

Life is better indeed!

---

