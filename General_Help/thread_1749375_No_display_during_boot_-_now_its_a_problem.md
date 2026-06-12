---
title: "No display during boot - now its a problem"
date: 2011-05-04
forum: General Help
---

### Post by speaktree on 2011-05-04
Hi all
 
I'm quite familiar with CentOS and have used ubuntu in the past, recently I decided to do a clean Ubuntu install and I've been running happily for about a week. That is until I decided to upgrade from 10.10 to 11.4. 
 
The first thing I've noticed since upgrading is that I can't see any part of the boot process as the screen just displays "Out of Range" until I'm shown the login screen, no boot selection and no display of drivers being loaded - which can cause problems when you need to troubleshoot. No worries I thought....
 
However, I noticed that since the upgrade moving windows around on the desktop was slow which is probably because I'm not using the right driver, so I decided to let it install the recommended driver.
 
Now I never see the login screen. It just keeps saying "out of range" for eternity. I've even tried booting into runlevel 1 - still the same thing. Do the drivers actually apply here?
 
I've also renamed my xorg.conf in an attempt to fix things - no luck.
 
Is there a way to get back from this without a reinstall? Any help will be gretly appreciated.

---

### Post by speaktree on 2011-05-05
I decided to do a reinstall - clean reinstall of 10.10 and then a straight upgrade to 11.4 (both 64 bit). Same problem with the screen not able to display during boot time. A slight difference this time round is that I could not boot into a Unity desktop but had to boot into classic. It also gave me a messahe saying that my system doesn't meet the requirements for Unity.

My system is as follows: CPU i5 760
                                         RAM 2GB DDR1333mhz
                                         Video adapter: Nvidia Geforce 7600GT

I think I should be able to run unity, but to be honest I don't know what the system requirements for it is. Should I try to download and install the driver from Nvidia's website? Or is the proprietary driver that ubuntu automatically wants to install the same one?

---

