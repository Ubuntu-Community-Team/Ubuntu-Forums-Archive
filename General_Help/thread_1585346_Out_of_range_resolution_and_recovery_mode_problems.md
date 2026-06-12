---
title: "Out of range resolution and recovery mode problems"
date: 2010-09-30
forum: General Help
---

### Post by skifer on 2010-09-30
Hey guys,

I decided to install ubuntu on my family desktop because it is quite old now and it needs constant maintenance for windows. I have used the old ubuntu on this computer some time ago i believe it was the 8.04 version. But anyway back to the point, i have decided to put ubuntu back onto the computer but i have encountered an issue. The issue is that when i installed ubuntu everything seemed to be working perfectly out of the box the printer, wireless etc... but when i installed the restricted drivers for the ati card inside. Upon loading ubuntu a big OUT OF RANGE came up on the monitor and i cannot access anything. I looked at the FAQ but am unable to get into recovery mode to type in the relevant command prompt and there seems to be no grub popping up to press esc/shift to get into the menu. Is there anyway around this? i am prepared to reinstall ubuntu but what could i do to prevent this upon re installation?.

Thanks for any help very much appreciated :)

---

### Post by skifer on 2010-09-30
I have now decided to reinstall ubuntu how can i prevent this from happening again when i install the drivers?

---

### Post by dino99 on 2010-09-30
remove xorg.conf, now the kernel directly deal with X

sudo rm -f /etc/X11/xorg.conf

reboot then check driver activation (system admin additional driver)

---

### Post by skifer on 2010-09-30
So basically type that command into the terminal, restart, install driver then it should work?

---

### Post by efflandt on 2010-09-30
"quite old" is a relative term that can mean a different time period for different people (5 years?, 10 years?).

How do you know if the proprietary ATI video you are trying to install even supports the card/chip that you have?  For example the X1300 on my desktop or work laptop is not supported by current ATI proprietary drivers, but both work fine with default ATI driver in 10.04 as long as I use **nomodeset** kernel boot parameter (since they do not seem to like the new kernel mode setting).

Which Ubuntu version did you install and what is the output of **sudo lspci -v** related to your video card?  If it is too old, you might just have to work without hardware acceleration.

---

