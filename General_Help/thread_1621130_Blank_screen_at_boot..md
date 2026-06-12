---
title: "Blank screen at boot."
date: 2010-11-13
forum: General Help
---

### Post by |{urse on 2010-11-13
Just upgraded from Karmic to Lucid.. Everything was running smoothly except compositing so I enabled the Open Source Edge repos and downloaded the latest driver my card (a ati radeon x1650). I rebooted to a bios splash and then nothing.. blank screen. After about 4 seconds of nothing the monitor flicks on showing the kubuntu bootsplash for a split second then blank again.

ctrl + alt + f$ isn't displaying a tty for me 
I'm not getting the usual grub menu on startup (esc isnt bringing it up)(it's a usb keyboard enabled in the bios)

What do I need to do once I boot to a livecd to rectify this? 

I miss having a .conf file for xorg. :(

---

### Post by |{urse on 2010-11-13
oh it's shift not esc.. solved

[http://melpctec.blogspot.com/2010/05/fix-ubuntu-1004-blank-screen-boot-up.html](http://melpctec.blogspot.com/2010/05/fix-ubuntu-1004-blank-screen-boot-up.html)

---

### Post by |{urse on 2010-11-14
Okay maybe not so solved..

Here's where I'm at so far..
All I get on login is a tty. So all I really need to do is get in with vesa or otherwise.

boot up with shift
highlight top entry in grub menu 
press e
remove "quiet" and "splash"
add "nomodeset" (xforcevesa doesn't work) where "quiet" and "splash" were
ctrl + x
sudo nano /etc/modprobe.d/kms-radeon.conf
> //contents of kms-radeon.conf
options radeon modeset=0
//this is so I dont have to edit my bootline every time i reboot
ctrl + x
sudo init 6 (reboot)

Well now here's the part where I thought things were solved.. however this just gets me a completely unanimated bootsplash. Just hangs there.

I think completely reinstalling xorg is going to be the way to go
so I edit my grub boot options to include nomodeset and prepare to reinstall xorg via command line. 

sudo ifconfig eth0 up
sudo dhclient
...
ping [www.google.com](www.google.com)
nooope
for some reason i'm not getting a lease
so much for reinstalling xorg with apt-get.

I'm going to do a fresh reinstall in about an hour unless someone can tell me how to use the kubuntu lucid install disk as an apt mirror from command line so I can reinstall xorg.

I suppose i could cd to the directory containing the .deb for xorg and dpkg -i that sucker but that doesn't give me the opportunity to apt-get remove --purge beforehand.

oh and when i do an apt-get $ I get lots of verbosity yelling about "something wicked happened while trying to" etc etc 

*holds os disk to computer's head*
Don't mess w/ me, I'll do it.

---

### Post by |{urse on 2010-11-14
Okay, fresh install.
Alas lucid you shall never know life on this machine.
Back to trusty Intrepid.
Maybe Meerkat will be better.

---

