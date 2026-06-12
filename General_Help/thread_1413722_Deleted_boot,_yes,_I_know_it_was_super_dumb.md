---
title: "Deleted /boot, yes, I know it was super dumb"
date: 2010-02-22
forum: General Help
---

### Post by molotschna on 2010-02-22
Let me walk you through my brilliance.

A few months ago my copy of XP crashed, so rather than fixing it I decided to come back to Ubuntu for awhile.  Set everything up as a dual boot, everything was fun, I just ignored XP.  Well today I pulled my HD, plugged it into a friends computer, replaced the XP file that had corrupted the system, and wanted to boot in XP.

This is where things get idiotic.

I realized that I hadn't been seeing a dual boot screen the whole time I had had Ubuntu.  I couldn't figure out how to get one, so my friend and I decided to replicate the XP problem on the Linux side of things, hoping it would block Ubuntu from loading so we could boot straight into XP.  So we deleted a few files from /boot/grub, thinking it would stop it from booting.  That didn't work.  So, we deleted /boot.

If you are smarter than we are, you now see that naturally Ubuntu didn't load, but instead froze up in what I assume is the grub loader.  We also didn't go into XP.  Instead, I am using the "try Ubuntu" option on the install CD.  There is no recover option on the CD as far as I can see

I have two questions:
1) How can I recover my Ubuntu system?
2) How can I bring up a dual-boot screen and boot XP?

Your help is appreciated.  

P.S. - I know our plan was a bad idea.  You can remind me if you feel it necessary.

---

### Post by HoboJ on 2010-02-22
Try this. [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

You'll want to scroll down to "Reinstalling GRUB 2 from the LiveCD".

---

### Post by molotschna on 2010-02-22
> **HoboJ said:**
> Try this. [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

You'll want to scroll down to "Reinstalling GRUB 2 from the LiveCD".


This didn't seem to work, at least not the way I understand it.  I know that the copy of Ubuntu I want to restore is on an "hda," and no hda's show up when I hunt for them through the "try Ubuntu" option.  Or is there a difference between the LiveCD this talks about and the option I'm using on the install?  Thanks!

---

### Post by oldos2er on 2010-02-22
You'll need to do much more than reinstall grub2; /boot contains your kernels, initrd.imgs, and other important configuration files. I think the easiest thing to do would be reinstall Ubuntu. If your XP partition wasn't shut down cleanly, Ubuntu may refuse to mount it or create a boot menu entry for it. If you need XP, you may want to repair it first, then reinstall Ubuntu.

---

### Post by falconindy on 2010-02-22
> **oldos2er said:**
> ...and other important configuration files.
Errr, the only config file I know of in the /boot directory is the kernel .config which is irrelevant for booting and day to day functions.


Assuming you haven't tried to reboot yet and you're still looking at your desktop...

```
sudo apt-get install linux-image-generic
sudo grub-install /dev/sda --recheck
sudo update-grub
```

That should cover everything you need to boot. If you need to do it from a liveCD, you'll need to establish a proper chroot to install the kernel and update grub (but not re-install grub).

---

