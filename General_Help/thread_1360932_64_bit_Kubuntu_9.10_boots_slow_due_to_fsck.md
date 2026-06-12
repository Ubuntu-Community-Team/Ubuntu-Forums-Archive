---
title: "64 bit Kubuntu 9.10 boots slow due to fsck"
date: 2009-12-21
forum: General Help
---

### Post by schmidtbag on 2009-12-21
I installed 64 bit kubuntu 9.10 on an AMD system about a month ago and upgraded the hardware to a newer AMD system without reinstalling.  everything works fine, but ever since i moved, the boot process is slower, but i noticed that it only slows down when fsck begins to run - which happens every time i boot.  it isn't saying the typical "computer has been booted 28 times - check forced".

i don't use a graphical loading screen because i like to see whats going on when my computer boots.  i guess all i'm wondering is how do i make it stop using fsck every time, or how can i make fsck run faster?

---

### Post by adam814 on 2009-12-21
What filesystem is being checked each time? If it's one of the ext filesystems (ext2, ext3, ext4) you can configure how often it is checked with this:

> tune2fs -c 28 -i 90 This would set it to be checked either every 28 mounts or 90 days, whichever comes first.  You could change it to whatever values you want.

---

### Post by schmidtbag on 2009-12-21
i don't think thats what i need, because thats for force check.  fsck is running whether its force check or not.  i'm using ext4

---

### Post by adam814 on 2009-12-23
Hmm...what do you have the pass value set to in /etc/fstab?   I think '1' is recommended for the root filesystem and higher values for others.  If you set it to '0' it shouldn't ever be checked automatically.

But then when it needs to be checked you'll have to do it from a LiveCD since you can't run e2fsck on a mounted partition and you can't unmount your root partition.

---

### Post by schmidtbag on 2009-12-23
hmm i'll have to look into that.  i'll check it in a bit, i just installed a new video card

---

### Post by schmidtbag on 2009-12-23
the pass was set to 1 and i changed it to 0 but it didn't do anything - everything else is also set to 0.

---

### Post by markofealing on 2010-01-07
I'm having exactly the same problem since upgrading from Kubuntu 9.04, also 64-bit on AMD Athlon 4200 x2 CPU. Every time I boot e2fsck is run. 

Also, sometimes then X loads the login screen, the screen is displayed briefly and then both monitors go blank. The OS is still running but all I can do is reboot in safe mode, login and manually startx, logout and reboot. It's then okay until the next time it goes wrong which is normally a couple of reboots later. I've just removed the login requirement to see if this improves matters (it's a home PC so no security issues!).

If this continues, I'm considering doing a fresh install as this behavior is really odd for Linux but have just noticed a new kernal update as I write so might hold fire!

---

### Post by schmidtbag on 2010-01-07
> **markofealing said:**
> I'm having exactly the same problem since upgrading from Kubuntu 9.04, also 64-bit on AMD Athlon 4200 x2 CPU. Every time I boot e2fsck is run. 

Also, sometimes then X loads the login screen, the screen is displayed briefly and then both monitors go blank. The OS is still running but all I can do is reboot in safe mode, login and manually startx, logout and reboot. It's then okay until the next time it goes wrong which is normally a couple of reboots later. I've just removed the login requirement to see if this improves matters (it's a home PC so no security issues!).

If this continues, I'm considering doing a fresh install as this behavior is really odd for Linux but have just noticed a new kernal update as I write so might hold fire!

i'd try the stuff everyone else in this post suggested, since you don't have exactly the same issue, just a very similar one.  what was recommended for me to do did not work (altho one did to some degree).  you're right tho, the problems you have are not very linux-like and to me and a fresh install imo is the best option, since you seem to have inconsistent problems

---

