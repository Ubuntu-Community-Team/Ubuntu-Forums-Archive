---
title: "Ubuntu Isn't Able To Boot"
date: 2010-01-15
forum: General Help
---

### Post by AdamGP on 2010-01-15
Hi,

   Yesterday I was trying to get the microphone to work in Skype by replacing pulseaudio with esound, as per here:

[http://www.econowics.com/news-from-the-net/170/skype-problem-with-audio-playback-ubuntu-810-intrepid-ibex/](http://www.econowics.com/news-from-the-net/170/skype-problem-with-audio-playback-ubuntu-810-intrepid-ibex/)

   Unfortunately, when I rebooted my computer I couldn't get Ubuntu to boot. GRUB loading, press 'esc' to enter menu shows up, then I get the following:

Boot from HD(0,0) ext 3 NUMBERS
Starting up...

[     3.944140] hub 5-0:1.0:  unable to enumerate USB device on port 1
/bin/sh: 1: runlevel: not found
*Reading files needed to boot...OK
*Setting preliminary keymap...OK
*Preparing restricted drivers...OK
*Setting the system clock...OK
*Starting basic networking...OK
*Starting kernel event manager...OK
*Loading hardware drivers...OK
*Setting the system clock...OK
*Loading kernal modules...OK
*Loading manual drivers...OK
*Setting kernel variables (/etc/sysct1.conf)...OK
*Setting kernel variables (/etc/sysct1.d/10-console-messages.conf)...OK
*Setting kernel variables (/etc/sysct1.d/10-network-security.conf)...OK
*Setting kernel variables (/etc/sysct1.d/10-process-security.conf)...OK
*Setting kernel variables (/etc/sysct1.d/30-tracker)...OK
*Setting kernel variables (/etc/sysct1.d/wine.sysct1.conf)...OK
*Activating swap...OK
*On battery power, so skipping file system check.
*Mounting local filesystems...OK
*Activating swapfile swap...OK
*Skipping firewall: ufw (not enables)...OK
*Configuring network interfaces...OK

init: rc-default main process (4311) terminated with status 127

And that's all. It just sits there. If I try booting with any of the other options from Grub, like the recovery modes, I get a lot more text but the same final product. Some of the numbers, like that of the main process or that of the USB port at the beginning vary with boot. I've also plugged it in to run a filesystem check but it ends up the same at the end. I'm running 8.10 on an Acer Aspire 4720. It's not dual-boot. Also, I couldn't boot from a Live CD. Again, the same thing happens. Does anybody know what's going on? Thanks in advance!

---

### Post by alwayshere on 2010-01-15
try booting to an older version in the boot menu it will be the 3rd one from the under your current versions recovery mode option

---

### Post by Leppie on 2010-01-15
> **AdamGP said:**
> [     3.944140] hub 5-0:1.0:  unable to enumerate USB device on port 1
what usb device was plugged in before rebooting?

> **AdamGP said:**
> I've also plugged it in to run a filesystem check but it ends up the same at the end.
what did you plug in?

---

