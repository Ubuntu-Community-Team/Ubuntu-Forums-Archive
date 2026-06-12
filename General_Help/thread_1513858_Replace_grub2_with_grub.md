---
title: "Replace grub2 with grub?"
date: 2010-06-20
forum: General Help
---

### Post by zong1 on 2010-06-20
Hi there,

  I have seen grub2 wreck the system console screen display, be dependant on files in /etc/default and /etc/grub.d and be exteamely hard to configure. Even worse Grub2 settings are distribution dependent and distribution specific. 

Something single like vga=nnnn in grub2 involves something akin to these commands in grub2 "set gfxmode=1280x800 set gfxpayload=keep insmod gfxterm insmod vbe" and editing far too many files.  I have a steady flickering screen loaded during boot because Ubuntu's usplash image is larger than 640x480 and the vga size is 640x480. Grub2 is reluctant to be anything but user friendly.

Practical question:
Does anyone know of a guide that could change grub2 back into the useful and user friendly grub (menu.lst).  

Regards.

---

### Post by wilee-nilee on 2010-06-20
Personally I think grub2 is much easier to deal with, I suspect a experience problem here but here is a link. Be very careful, if you end up with both grub type files in the OS it will be a mess. I really think you should ask for help on grub2, setting the screen size is easy for one.
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

This is first stanza is a good one, and this person who built this link knows their stuff.

> Someone will undoubtedly ask, "why would I want to revert to legacy grub"? My answer is, "I hope you don't". Grub 2 is the way of the future and I'd bet that a year from now nearly everyone will think of legacy grub as downright prehistoric! If you're new to Ubuntu I believe you'll find Grub 2 to be no more complicated than legacy grub, and the documentation continues to improve. I know 20 months ago legacy-grub was confusing to me.

---

### Post by ronnielsen1 on 2010-06-20
Have you looked at Burg? Not really a replacement but more of a cover for it. Has about 7 different themes 

[http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html](http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html)

---

### Post by zong1 on 2010-06-20
Burg does look very nice, but I have a desire of keeping the boot process as graphic free and simple as possible.  Also, I admit I like to use something I can understand at 3 in the morning.

wilee-nilee, Thank-you very much for the URL to the grub2/grub-legacy replacement.

---

### Post by wilee-nilee on 2010-06-20
> **zong1 said:**
> Burg does look very nice, but I have a desire of keeping the boot process as graphic free and simple as possible.  Also, I admit I like to use something I can understand at 3 in the morning.

wilee-nilee, Thank-you very much for the URL to the grub2/grub-legacy replacement.

I never even tried to understand grub-legacy so I'm grub2 centric. Good luck.:p

---

### Post by zong1 on 2010-06-21
Hi,
  Actually I had some interesting results.   I used the startupmanager to see what it said, and it has an option to set the console resolution.  It was set to 640x480, which is not what I want, so I changed it to 1024x768.

I rebooted, and grub complained the vga=nnnn was depreciated and that GFXnnnnn=1024x768x8,1024x768 should be used.  

This means that startupmanager is not fully grub2 compliant because it attempts to add the vga=nnn command instead of the GFX style for grub2.
The bonus is that although the command failed, grub2 could not determine the console resolution and defaulted to a dumb tty, which meant the screen text displayed in ASCII. Perfect because now there is no horrible flickering, and I can enter the dmcrypt passphase without being strobed to death.

After this, I edited /etc/default/grub and removed the vga=nnnn from the GRUB_CMDLINE_LINUX=""  line., and added the GFXnnnnn=1024x768x8,1024x768 (I am typing this from memory so cannot remember the exact GFX command).  Also I tried entries like GRUB_GFXPAYLOAD_LINUX=1024x768x8, which failed.  Rebooting brought back the flickering 640x480 screen.  

Also, I tried uncommenting #GRUB_TERMINAL=console , but grub2 in Ubuntu ignores this setting so it went back to the 640x480 flickering mode.

In the end, I added  GRUB_CMDLINE_LINUX=" vga=666 " 
This gives the depreciated message on boot, but it forces Grub to disable the graphics mode, so all is well. 

Why does it flicker: I suspect that this is because the usplash image is larger than 640x480, and has some animation.  Screen update and resolution cause it to flash.

Summary. 
Yes, grub2 may well be the way forward, but as far as I can tell, it introduces too many dependencies, is convoluted, and has been poorly implemented into Ubuntu.  I shall carry on using it so that I can get to grip with it.  I do hope that Novell does not go the grub2 way, because I actually have to support SLES in my real job.  Luckily, SLES11 still uses normal grub. Phew.

---

### Post by wojox on 2010-06-21
Grub2 is awesome. Just take a few days to work with it. Have a look here if you still want to purge it [https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202)

---

