---
title: "Ubuntu crashes on boot"
date: 2010-05-04
forum: General Help
---

### Post by quasar9011 on 2010-05-04
sorry for double posting.  got no reply on Kubuntu thread.  

I have been using DELL Latitude D400 laptop for 9.10 and prior versions.   I thought I would give it a try with the 10.04 release.  This was a  disaster.  After close to 2 hours upgrade, my boot loader has the  followings with other recovery options.

Ubuntu 10.04 LTS Kernel 2.6.32-22-generic 
Ubuntu 10.04 LTS Kernel 2.6.31-21-generic.  

When I boot to the 2.6.32-22, the Kubuntu logo would cycle through the 5  red dots.  Eventually the screen would crunch into tiny dots or just a  green band about 1 inch in height.  

I also tried the CD installation and the installation screen just went  blank even with NOPCI=off, NOAPIC, and NOLAPIC checked.  The Boot  options is 

file=/cdrom/preseed/ubuntu.seed 
boot=casper only-ubiquity 
initrd=/casper/initrd.lz quiet splash

I also added -- vga=771 at the boot options line without checking the F6  Other Options. With that I got an error:

[131.600286] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw"  not found or load failed.

I checked the /lib/firmware/ and I have both b43legacy and b43 folder  with all the files in them.  

Does it matter that I have Kubuntu and trying to install with Ubuntu CD?

---

