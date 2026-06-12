---
title: "slow and messy GRUB in 12.04"
date: 2012-05-08
forum: General Help
---

### Post by Pablo W on 2012-05-08
Hello,
I'm having a very slow and messy boot in an HP Compaq dc7700 Small Form Factor with a freshly installed Ubuntu 12.04 as the only operating system.

I have already tried boot-repair with no success. I have installed Grub Customizer, but I don't know what to do with it.
grub is updated and I have both 3.2.0-23 and the 3.2.0-24 kernels.

I think the problem could be in something related to Flexnet. I don't know what Flexnet is, but when I ran 

sudo grub-install /dev/sda

the outcome was:
```
Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *        2048   152158207    76078080   83  Linux
/dev/sda2       152160254   156301311     2070529    5  Extendida
/dev/sda5       152160256   156301311     2070528   82  Linux swap / Solaris
pablo@pablo-HP-Compaq-dc7700-Small-Form-Factor:~$ sudo grub-install /dev/sda
/usr/sbin/grub-setup: aviso: Sector 33 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.
```

Any help will be much appreciated.

---

### Post by 2F4U on 2012-05-08
For information on what FlexNet is read this article from Wikipedia

[http://en.wikipedia.org/wiki/Flexnet](http://en.wikipedia.org/wiki/Flexnet)

The article mentions that the software is known to cause problems with bootloaders, so it may very well be the reason for your problem.

---

### Post by Pablo W on 2012-05-08
Thanks 2F4U for the background info. I'm still looking for a solution to this.

---

### Post by 2F4U on 2012-05-08
My question would be were does that software come from? It is certainly not part of Ubuntu, so you first should find out why it is there and then for what it is used.

---

### Post by Pablo W on 2012-05-08
Thanks again, 2F4U.
I know very little of Ubuntu, but since I made a fresh install, I don't know where to start from. Isn't it true that if you make a fresh install from a properly created usb drive everything that you have in your hard drive comes from Ubuntu?


Aside from this issue, Ubuntu is running with no major problems.

---

### Post by oldfred on 2012-05-08
A lot of Windows proprietary software uses flexnet for DRM - digital rights management.

Adobe Photoshop, CAD/CAM, Rosetta Stone, Matlab others 

One user posted this:

Sector 32 is already in use by FlexNet
[http://www.amazon.com/Adobe-Photoshop-Extended-CS4-VERSION/product-reviews/B001EUDGO2](http://www.amazon.com/Adobe-Photoshop-Extended-CS4-VERSION/product-reviews/B001EUDGO2)
The problem turned out to be Adobe's digital rights management software [DRM]. Do your own search for "FlexNet," formerly known as "SafeCast." What I have read is that FlexNet is a viral rootkit that replicates in multiple locations whenever a CS3 or CS4 product is installed, including trial versions.
Erase flexnet, if not using protected windows software anymore:
[http://ubuntuforums.org/showthread.php?t=1661254](http://ubuntuforums.org/showthread.php?t=1661254)

Grub2 originally was writing into the same sectors as flexnet, but then they modified grub as a work around, since Windows was not going to do a work around. The area after the MBR was by convention used for more boot code but the DRM folks decided to use it also.

---

### Post by Pablo W on 2012-05-08
> **oldfred said:**
> A lot of Windows proprietary software uses flexnet for DRM - digital rights management.

Adobe Photoshop, CAD/CAM, Rosetta Stone, Matlab others 

One user posted this:

Sector 32 is already in use by FlexNet
[http://www.amazon.com/Adobe-Photoshop-Extended-CS4-VERSION/product-reviews/B001EUDGO2](http://www.amazon.com/Adobe-Photoshop-Extended-CS4-VERSION/product-reviews/B001EUDGO2)
The problem turned out to be Adobe's digital rights management software [DRM]. Do your own search for "FlexNet," formerly known as "SafeCast." What I have read is that FlexNet is a viral rootkit that replicates in multiple locations whenever a CS3 or CS4 product is installed, including trial versions.
Erase flexnet, if not using protected windows software anymore:
[http://ubuntuforums.org/showthread.php?t=1661254](http://ubuntuforums.org/showthread.php?t=1661254)

Grub2 originally was writing into the same sectors as flexnet, but then they modified grub as a work around, since Windows was not going to do a work around. The area after the MBR was by convention used for more boot code but the DRM folks decided to use it also.

Thanks, oldfred, for a very useful post.
I have posted a specific question in the thread you referred me to ([http://ubuntuforums.org/showthread.php?t=1661254](http://ubuntuforums.org/showthread.php?t=1661254)) and will come back here with the outcome as soon as I get help there.

---

### Post by Pablo W on 2012-05-09
Update:

Following olfred's advice, I applied the how-to posted in this forum: [http://ubuntuforums.org/showthread.php?t=1661254](http://ubuntuforums.org/showthread.php?t=1661254) and the problem was solved. So, a big thank you to oldfred. You saved me twice this week!

The whole experience taught me something that maybe is obvious for many people, but I didn't know: fresh installs from a usb drive do not wipe out the whole disk (as you might suppose from the installation options) even if you choose Ubuntu to take the whole drive (rather than installing it side by side another operating system).

More interestingly, the messy boot problem was not there while I used Ubuntu 12.04 beta 2. It only appeared when I decided to do what you are supposed to do: a fresh install rather than an upgrade. So this brings me to the question of how to safely upgrade from an advanced beta version once the Long Term Release is out the next time (if needed at all). But this is probably a question for a different room in this forum.

Thank you all. With great pleasure, I've marked this thread as solved.

---

