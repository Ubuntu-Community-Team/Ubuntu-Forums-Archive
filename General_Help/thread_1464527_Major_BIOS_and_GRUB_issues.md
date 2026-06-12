---
title: "Major BIOS and GRUB issues"
date: 2010-04-28
forum: General Help
---

### Post by Mars92 on 2010-04-28
Wasn't really sure where to post this, or if this is even the right forum for it, but I figured I'd try anyway.

I been having so pretty major problems with my computer, mainly due to me tampering with stuff I don't know much about. It's long.

It started when I tried installing patched OS X DVD I had downloaded to try out (if it worked i was planning on buying the physical copy to make things a little more legal). I was following an installation guide I found online, and it asked me to make a new partition, then mark it as active. I did this and it prompted me something about having an operating system on the marked partition, so I figured it was fine because the quide said so, and I was about to install an OS anyway. 

Then I restarted and attempted to install, but after multiple tries I gave up and tried to boot back into Windows. On boot i was told that the BOOTMGR was missing, but because I didn't have a Windows 7 disc to repair it (got the legal code from my brother), I installed Ubuntu Studio 9.10 onto what was the OS X partition, figuring this would be a good opportunity to get GRUB as the default bootloader. Boot then said that the OS was missing, but I knew it wasn't so I had to F12 and select the drive manually, which has worked so far, but it's a real pain, especially now that Ubuntu is the default in GRUB, so I have to go through another menu when I boot.

also, I tried changing the default boot of GRUB, by editing etc/default/grub (and yes, I did run update-grub after saving it) and now when I try booting Windows it says it has an "invalid signature", which means I can't even get into Windows anyway, I googled the problem but all the answers seem to really only be relative to the person asking.

Any light you can shed is greatly appreciated.

---

### Post by SlugSlug on 2010-04-28
I'd look at BIOS hard drive boot prioty and set them to PM; PS, SM; SS; and try follow suit for SATA drives,

then reinstall grub

---

### Post by Mars92 on 2010-04-28
With my limited knowledge that sounds good, but I don't really know how to do that. If I could get some more detail that might help.

---

### Post by SlugSlug on 2010-04-29
If your unsure about BIOS then leave that bit, as for reinstalling grub there are loads of guides all pretty easy to follow, here's one 
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Mars92 on 2010-04-29
Thanks I got windows working again in GRUB, so now all thats left is the BIOS.

---

### Post by SlugSlug on 2010-04-29
grubs working \ windows working\ ubuntu working?

if so leave bios

---

### Post by Mars92 on 2010-04-29
Theyre all working now, but its such a pain to have to go through 3 menus during boot.

---

### Post by SlugSlug on 2010-04-29
3 menus?

what are they

---

### Post by Mars92 on 2010-04-29
Well, I have to go press F12 t oget to the boot menu, find the right HDD, go to GRUB, go down to Windows (I'd rather it be default, since I only use ubuntu for studio operations. But I'm pretty sure trying to change the boot order of GRUB is what gave me the signature issue) then i have to select the account I want to log in as (which I'm not sure why this is, since I only have 1 account. XP used to do this for me too).

---

### Post by whiskeytango73 on 2010-04-29
use Hiren's Boot CD to wipe drive - start over clean

---

### Post by oldfred on 2010-04-29
Run this so we can see where everything is installed:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

