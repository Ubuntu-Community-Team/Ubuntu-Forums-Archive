---
title: "windows do not disappear"
date: 2010-07-01
forum: General Help
---

### Post by ubtraut on 2010-07-01
Hi all,

I just upgraded to ubuntu 10.04

Update worked well. But now the windows do not close properly, but remain as an inactive background display.

As a side note, there's no startup screen, but just some screen garbage, as if an incorrect video driver would have been used. 

When I do move windows, their shade remains in the background, filling the background with garbage.

Any idea?

Thanks!

---

### Post by dino99 on 2010-07-01
sudo rm -f /etc/X11/xorg.conf

check your synaptic repo to use only genuine ubuntu repo from main server (no mixed distro)

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

check driver activation: system admin hardware driver

you can clean the system too with gconf-cleaner and bleachbit

---

### Post by ubtraut on 2010-07-01
Thanks, but I did not see any positive improvement.

It worked for a while (although it sometimes started without a gui at all, but offering just a full screen text login) - and now it fell back to the former malfunction.

It's an outdated Medion MC 96500 laptop (2004?) with ATI M26 (Radeon Mobility X700 XL (PCIE)) - I'm afraid there's no better graphics support.

I now added radeon.modeset=1 to the end of the line GRUB_CMDLINE_LINUX_DEFAULT from /etc/default/grub , but it did not improve the video malfunction.

I did not see any special trouble reports in Xorg.0.log or syslog, but I know little about that stuff.

---

