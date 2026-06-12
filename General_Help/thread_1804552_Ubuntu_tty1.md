---
title: "Ubuntu tty1"
date: 2011-07-14
forum: General Help
---

### Post by kalaharigreen on 2011-07-14
Hello ubuntu adventurers,
I need help please. Ubuntu 11.04, after grub I get the tty1 with login and password. After I login I get the command line. All I want is my gui back. After waiting some time I get a message have 31 packages available for install. I am running apt-get upgrade as I type this, hoping it will bring my gui back.

I am using compaq V3000 with AMD64 turion x2, Nvidia graphics card. Yesterday I was using an LCD projector and may have upset the screen resolution settings while trying to get the projector to display my screen.

Why did my computer suddenly decide to use tty1 instead of loading the unity gui, which I quite like except for a few little glitches?

Thanks in advance:confused:

Yep: I still have tty1 when I start up. I wouldn't mind if I new how to get the gui up?

---

### Post by Atamisk on 2011-07-14
Are there any issues or errors when you try to start X(xinit)? 

Where did your Nvidia graphics drivers come from? if you got them from Nvidia, they are kernel specific, and you need to re-install with each kernel update. did you update recently? 

HTH

--Aaron

---

### Post by kalaharigreen on 2011-07-14
I tried startx & and came up with error Fatal server error: no screens found

---

### Post by Atamisk on 2011-07-14
I see... In my experience that means there's no driver that wants to run your graphics card. Did you install graphics drivers manually, or did 'Additional drivers' do it for you?

If you installed the drivers manually (from NVidia's website):
Try re-installing the driver. the driver builds a kernel module that stays with THAT kernel. so, when you update kernels, the driver "breaks". 

If you installed them from 'Additional Drivers' menu
Make sure the package nvidia-common is intact and up to date.

---

### Post by kalaharigreen on 2011-07-14
Hi Aaron,
I've been upgrading thru several releases. the only driver I remember installing was for the wireless. I see at the bottom of my screen several sudo apt-get lines that change when I press up or down arrow. I must have messed things up when I was playing with the x server settings yesterday.

thanks

doug

---

### Post by kalaharigreen on 2011-07-14
[http://ubuntuforums.org/showthread.php?t=1629619](http://ubuntuforums.org/showthread.php?t=1629619)
I will now try to edit at grub as per the above link.

---

### Post by Atamisk on 2011-07-14
Entirely possible. However, new X versions won't need the Xorg.conf file to run, and only reference it if it's actually there. If you think something got messed up there, try renaming it to get it out of the way. Then reboot to see if it works.

---

### Post by kalaharigreen on 2011-07-14
Thanks, I will follow your instructions. How do I rename Xorg.conf? Appreciate  your help!!

---

