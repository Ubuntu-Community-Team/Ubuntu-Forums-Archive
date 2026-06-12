---
title: "Had a grub out of disk error and now everything is screwy; did I install incorrectly?"
date: 2011-12-03
forum: General Help
---

### Post by BloomingNutria on 2011-12-03
Hi everyone. I'm running a two-day-old installation of Xubuntu 11.10 that booted just fine the first few times, and then suddenly I had some trouble where I could not boot (it's quasi-fixed now). When this happened, I had not installed anything or made any changes at all that I can think of since the last time I booted. I got a message that said 

error: out of disk 
grub rescue> 

According to the grub 2 guide ([https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting](https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting)), this error appears when grub 2 cannot find the grub folder, the grub.cfg file, and the associated modules. The guide gives instructions for booting from this grub rescue prompt, which I followed. Here is what I entered exactly:

set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
insmod normal
normal
ls /boot
insmod linux
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot

And it booted. However, lots of things seems to be messed up now. First, my display settings appear to be different. All the icons and windows have been stretched slightly so that the windows themselves are wider, and so are the gaps between characters. My monitor settings have not been changed. In addition, the random screensaver mode cannot find many of the screensavers. It can find at least one of them, but when it tries to display others, I see a nearly blank screen with just a few small ultra-small lines of type in the corner which say something about it not being able to find them (I can't seem to get this to come back so I can read it). Also, I can no longer play video files, nor can I mount my external hard drive (it says the deamon is inhibited).

So I'm actually hoping someone can explain a couple of things to me. Namely, what exactly happened to cause all of these problems, and why would this grub error occur in the first place? According to the grub 2 guide: “A common reason for the grub rescue> prompt is an incorrect path to the grub folder. Reasons for the prompt could include a failure to update GRUB 2 after certain system or partition operations, improper designation of the grub folder location, or a failed installation.” So this means that there was a problem with my installation? If that is so, then what? And why would everything boot fine the first few times and then all of a sudden have this problem finding the grub folder, the grub.cnf file, etc.?  I am really hoping someone can shed some light on this for me, because I think I am going to reinstall after this weirdness and I do not want to make the same mistake that caused the problem this time. Also, I would just really like to understand what is going on. Here is what my partition structure looks like:

[http://img39.imageshack.us/img39/1475/partitionscreenshot.png](http://img39.imageshack.us/img39/1475/partitionscreenshot.png)


Did I make some error here? Any help would be appreciated!

Thanks to all for sharing their knowledge.

---

### Post by Dlambert on 2011-12-03
My friend had the same thing with xubuntu, but not with ubuntu...wierd.

---

### Post by BloomingNutria on 2011-12-03
> **Dlambert said:**
> My friend had the same thing with xubuntu, but not with ubuntu...wierd.

Yeah, I never had it with Ubuntu 10.04 either.

---

### Post by BloomingNutria on 2011-12-04
Well I reinstalled, keeping my home folder, and everything went back to normal. I also added a boot partition and put grub in the Master Boot Record (just like it was before). I'm not sure if this will have the effect of properly defining a path to the grub folder (can anyone tell me?), but from what I have been able to learn, it seems to be a good partitioning scheme. 

Still hoping to get some input on the cause of this. 

Thanks to everyone for sharing their knowledge.

---

### Post by *^kyfds( on 2011-12-04
it seems very strange that it happens on some OS's, but not others...

that'll make an interesting read-up

---

