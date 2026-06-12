---
title: "No menu.lst in my /boot/grub"
date: 2010-01-02
forum: General Help
---

### Post by cjwescott on 2010-01-02
Trouble shooting my wireless card connectivity and one suggestion in the Ubuntu documentation is to add pci=noacpi to my boot kernel.  Additional searches to actually determine what this means leads me to editing my menu.lst in my /boot/grub.

I have no menu.lst in my /boot/grub directory.

What am I missing.  Is the file now called something else in 9.10? or is it located somewhere else?

---

### Post by Cheesemill on 2010-01-02
Ubuntu 9.10 now uses Grub2 instead of Grub which doesn't use menu.lst anymore.
See the following threads for more info:

[http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Leppie on 2010-01-02
> **cjwescott said:**
> Trouble shooting my wireless card connectivity and one suggestion in the Ubuntu documentation is to add pci=noacpi to my boot kernel.  Additional searches to actually determine what this means leads me to editing my menu.lst in my /boot/grub.

I have no menu.lst in my /boot/grub directory.

What am I missing.  Is the file now called something else in 9.10? or is it located somewhere else?
karmic ships with grub2 which uses grub.cfg. however, it's better to not edit this file manually.
if you want to set default boot parameters, edit your /etc/default/grub file. Edit the following line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to something like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=noacpi"
```
then run update-grub to regenerate your grub.cfg:
```
$sudo update-grub
```

---

### Post by cjwescott on 2010-01-02
Thank you both.  Very informative posts.

Unfortunately adding the statement of pci=noacpi made no difference in the outcome.  I still have an _active_ wireless connection which does not allow any transmission of data to/from my router.  Browser is dead and so is my Synaptic Package Manager from reloading.

I don't know how to proceed and trouble shoot this issue.  My iwconfig lists the following for wlan0:

IEEE 802.11g      ESSID: off/any
Mode:  Managed  Frequency: 2.437 GHz  Access Point:  Not-Associated
Bit Rate: 54 Mb/s
Power Management: off
Link Quality: 0 Signal Level: 0  Noise level: 0
Rx invalid nwid:0 Rx invalid crypt: 0  Rx invalid frag: 0
Tx excessive retries:0 Invalid misc:0 Missed beacon: 0

---

