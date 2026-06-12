---
title: "Ubuntu 9.04 not in GRUB, although installed"
date: 2011-09-25
forum: General Help
---

### Post by Karljv on 2011-09-25
Hello
 
My problem->
 
I installed ubuntu 9.04 and all went well, I also partitioned my HDD. I made an user wit a password and logged in. Rebooted, Ubuntu was in GRUB and everything went just swell. Then I wanted to modify a few files to get my D-Link DWA-125 working and after that, when i rebooted, Ubuntu was no longer bootable in GRUB (memtest and Windows 7 remained there). How can I get Ubuntu back into GRUB? Sorry I'm new to this whole Linux thing.
 
Now as to what I did to get D-Link working, but which instead destroyed something else!
--------------------------------------------------
 
Code:
sudo gedit /etc/modprobe.d/blacklist.confAdd three lines:
Code:
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00libProofread carefully, save and close gedit. Remove ndiswrapper completely, if you installed it:
Code:
sudo apt-get remove --purge ndiswrapper*Uninstall any drivers you compiled from source:
Code:
cd Desktop/2009_RTL3070etc.Change to the directory of whatever file you compiled.
Code: 
 
and
 
Code:
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1", ATTR{idProduct}=="3c16", RUN+="/sbin/modprobe -qba rt3070sta"
Proofread twice, save and close gedit.
Code:
sudo gedit /etc/modprobe.d/network_drivers.conf
Add one long single line:
Code:
install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "07d1 3c16" > /sys/bus/usb/drivers/rt2870/new_id

---

### Post by oldfred on 2011-09-25
I know video gets compiled into the kernel, so as part of the uninstalls did your kernel get uninstalled?

If you have 9.04 it used grub legacy. But is was only supported until Oct 2010.

[http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases](http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases)

You may be able to change update manager to use just the CD to reinstall a kernel from a liveCD, but I have never done that. 

I think it is time to upgrade.

---

