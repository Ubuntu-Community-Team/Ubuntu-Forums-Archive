---
title: "[xorg/nvidia]xserver starts, but no image"
date: 2005-02-04
forum: General Help
---

### Post by GoldieLox on 2005-02-04
Hi, I just installed Ubuntu this week and after upgrading to "hoary" I wanted to install the latest nvidia driver, so I followed the HOWTO on this forum to the letter... ([http://ubuntuforums.org/showthread.php?t=12823](http://ubuntuforums.org/showthread.php?t=12823))

Everything went fine:
my new kernel (2.6.10) boots just fine
I editted my xorg.conf as instructed
I checked whether the proper nvidia kernel modules were loaded (lsmod | grep nvidia) -> they weren't, so I did as the HOWTO suggested -> success.

So, I started the xserver: startx

My monitor goes in standby mode, but I hear the sounds playing through my speakers that gnome is starting just fine.... But no screen...

hitting ctr-shift-f1 has no effect, i can't get a login screen, my monitor stays blank... :(

I have no idea what went wrong; I'm quite sure everything went fine, no errors, nothing in my xorg.conf looks weird.

Specs:
Ubuntu warty upgraded to hoary
nvidia geforce 5900xt connected through a DVI cable to a 19" TFT:
1280x1024@60Hz.

I would like to post my config files or log files, but since I have no working X server, I have to use Windows....

Suggestions?

P.S. I have yet to try setting the driver back to "nv" instead of "nvidia". X would probably start normally that way...

---

### Post by Forl on 2005-02-13
I have the same problem with XFee86, also using a TFT with DVI.
Anyone got a solution?

---

### Post by grj on 2005-02-13
You do not need to install nvidia drivers following that how-to. They are now in the latest restricted modules. Do an 

apt-get update
apt-cache search nvidia
apt-get install <the restricted module here>

On my computer, ctrl+alt+fn, does not work with the nvidia driver. The screen displays strange lines.

---

### Post by Forl on 2005-02-13
[QUOTE=grj]You do not need to install nvidia drivers following that how-to. They are now in the latest restricted modules. Do an 

apt-get update
apt-cache search nvidia
apt-get install <the restricted module here>

On my computer, ctrl+alt+fn, does not work with the nvidia driver. The screen displays strange lines.[/QUOTE]But I used the restricted module.
I'm quite sure the drivers work, it just seems lika the DVI-output has been disable, I'll try VGA later.

---

