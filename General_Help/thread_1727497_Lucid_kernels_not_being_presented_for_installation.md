---
title: "Lucid kernels not being presented for installation"
date: 2011-04-12
forum: General Help
---

### Post by Cavsfan on 2011-04-12
Just curious as to why this would be happening, but I had been running on the Lucid kernel 2.6.32-28-generic.
And when I looked in Synaptic, I noticed there were kernels 29 and 30 available.

I manually installed them and deleted the older ones I had - 27 and 28.

I believe I have all of the generic Lucid software sources and I get updates for everything else.
Just curious as to why these kernels were not available to be installed automatically.

I have never seen this happen before.
Any explanation as always is much appreciated.

---

### Post by d3v1150m471c on 2011-04-12
I want to say those are from maverick's backports and not considered an upgrade. I could be wrong, though.

---

### Post by lithopsian on 2011-04-12
They aren't backports, but they are a different package and not an updated version of a package you already have.  This is to enable you to have multiple kernels installed, and also to avoid trashing your whole system by replacing a working kernel with one that might not work.

---

### Post by d3v1150m471c on 2011-04-12
yeah normally the kernel updates come 'linux-image-generic', if i'm not mistaken. it's all coming together now 0_o lol

---

### Post by Cavsfan on 2011-04-12
AFAIK this is the default kernel for Lucid. I initially had 
**linux-headers-2.6.32-26 **
**linux-headers-2.6.32-26-generic** and
**linux-image-2.6.32-26-generic**
as the parts of the kernel and then that was updated to 32-27.

I did notice I had 
**linux-headers-2.6.32-30 **
**linux-headers-2.6.32-30-generic**
But not **linux-image-2.6.32-30-generic** so I removed them before manually re-installing all 3 files.
Which is why I was running 32-28 instead of 32-30 (the latest).

I had gotten an automatic upgrade to a kernel before, which is why I was wondering why I didn't get the 32-29 kernel.

So, if I make **10_linux** executable in grub, with this command:
```
grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0
```
I get these options: (Both kernels I installed manually)

```

     0	Ubuntu Lucid Lynx
     1	Ubuntu Lucid Lynx (Recovery Mode)
     2	Windows 7
     3	Ubuntu, with Linux 2.6.32-30-generic
     4	Ubuntu, with Linux 2.6.32-30-generic (recovery mode)
     5	Ubuntu, with Linux 2.6.32-29-generic
     6	Ubuntu, with Linux 2.6.32-29-generic (recovery mode)
cavsfan@cavsfan-desktop:~$ 
```

---

### Post by Cavsfan on 2011-04-21
Ironically, I got the 2.6.32-31 kernel upgrade today...

---

### Post by Cavsfan on 2011-09-30
I got the linux-headers-2.6.32-34 kernel today along with version 7.0.1 of FF.
But, again for some odd reason I had to go to SPM to find the missing piece and install it from there.
Prior to doing so, the 34 kernel did not show up and no restart was needed.
But, all is well now. After I installed the missing piece from SPM, I could see that it built my nVidia driver 
(had to click on show details to see the "SUCCESS") and a reboot was required.

Just glad I knew what to do.
Now I'm going to check if my nVidia driver needs updating.
Which will require the kernels to be removed and then reinstalled.
Still loving Ubuntu! :D

---

### Post by CatKiller on 2011-10-01
You've probably removed one of the Linux meta-packages - linux-image, probably.

As has already been said, kernel packages are classed as different packages rather than different versions of the same package so that you can keep the old one when you install the new (so that your computer remains bootable if the upgrade goes horribly wrong). So that you get upgrades there are a set of meta-packages whose only role is to depend on the latest version.

Grub should be updated automatically by the install scripts. You shouldn't need to do it yourself.

---

### Post by Cavsfan on 2011-10-02
> **CatKiller said:**
> You've probably removed one of the Linux meta-packages - linux-image, probably.

As has already been said, kernel packages are classed as different packages rather than different versions of the same package so that you can keep the old one when you install the new (so that your computer remains bootable if the upgrade goes horribly wrong). So that you get upgrades there are a set of meta-packages whose only role is to depend on the latest version.

Grub should be updated automatically by the install scripts. You shouldn't need to do it yourself.

Actually, I didn't remove anything. It has been doing this for the past few kernel installs. I have to go find the missing piece.
After the updates occurred, Grub did not update or anything and I was left running on the 33 kernel.

I do see in SPM under Missing Recommends - linux-headers-generic 
We'll see upon the next kernel install if adding that fixes the problem.

Thanks CatKiller :)

---

### Post by Krytarik on 2011-10-02
> **Cavsfan said:**
> I do see in SPM under Missing Recommends - linux-headers-generic 
We'll see upon the next kernel install if adding that fixes the problem.
In addition to that, definitely make sure that the meta-package "linux-image-generic" is installed as well, as already indicated *twice* before!

Greetings.

---

### Post by Cavsfan on 2011-10-26
I am pretty sure this was involved with removing and re-installing kernels to get them to build the new nvidia driver into the kernel.

Apparently, (as stated above) more than just the 3 kernel files get removed when you remove the only kernel you have.

I will see how it goes when the next new kernel gets installed and resolve this thread.

---

### Post by Cavsfan on 2011-11-09
Just got an update with new install kernel 2.6.32-35-generic and everything went smooth.
So, this problem was caused by me removing the only kernel left on my system in order to get the nvidia script to install the driver in the kernel.

This time, I only removed 2.6.32-33-generic. I didn't remove the most current kernel 2.6.32-34-generic.

I manually installed the driver in 2.6.32-34-generic and the script just installed the video driver in 2.6.32-35-generic.

Issue resolved

Thanks and sorry if I wasted any one's time on this. :)

---

