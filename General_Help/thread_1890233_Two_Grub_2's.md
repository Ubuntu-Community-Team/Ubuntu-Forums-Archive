---
title: "Two Grub 2's?"
date: 2011-12-03
forum: General Help
---

### Post by danageis on 2011-12-03
So here is my predicament:

I have a triple boot system with Windows 7, OS X and Ubuntu 11.10 all installed to booted through Grub 2 on the MBR.

I am using GRUB 2 because of the awesome password protection thing before you load up any OS. However, i would really like to use Chameleon.

My idea was that I could have a single entry in GRUB on the MBR that chainloads Chameleon. This works fine except that if I pick Ubuntu's partition from the Chameleon menu, it chainloads back to the GRUB MBR install.

So, I was wondering if there was a way to put a GRUB install on my Ubuntu **partition** to chainload to in Chameleon, while still having a different GRUB on the MBR.

I've read about this being possible when you have 2 different Linux partitions, but I only have Ubuntu.

I was thinking there might be a way if I had the MBR GRUB 2 on a /boot partition (I have never made one before) and the GRUB for Ubuntu on my Ubuntu partition. Would that work?

Sorry if this is a bit complicated, but if anybody could help me out with this I would greatly appreciate it :)

---

### Post by psihokiller4 on 2011-12-03
I'm not very expert here but I know few things

1. let say we have 3HDD

1. HDD windows
2. HDD linux
3. HDD OS X

if you have grub configured for 3 OS - es only in OS X and have configured in bios for master 1. or 2. HDD you won't get choice to start OS X but instead it'll automaticly start windows or ubuntu

that depends on witch HDD has priority boot

---

### Post by danageis on 2011-12-03
Er, I don't really know what you were trying to say but thanks for trying to help. Anyways, I figures it out: I made a dedicated GRUB partition that has GRUB for the MBR and automatically chainloads to Chameleon while prompting for password.

The GRUB install from my Ubuntu partition is still intact and now when I select the Ubuntu partition from Chameleon it loads Ubuntu.

---

