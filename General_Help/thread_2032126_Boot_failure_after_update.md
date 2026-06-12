---
title: "Boot failure after update"
date: 2012-07-23
forum: General Help
---

### Post by Katla on 2012-07-23
I just updated the latest package that was available with the manager. Headers and whatnot. Was prompted to restart the system, which I did. Ubuntu tries to load but all I get is the blank purple screen. Have rebooted numerous times, no change. How do I get it back? Am on 12.04 and have a flash drive containg 10.something, if that is any help.

As an aside, I am starting to doubt the wisdom of ever updating Ubuntu. It almost always seems to make things worse.

Any assistance is greatly appreciated.

---

### Post by Katla on 2012-07-23
Update: after having posted the above on my phone, I rebooted one more time and got results. So while the main issue is "solved", that still leaves me with the issue of not trusting Ubuntu to boot properly. 

I'd still appreciate some troubleshooting tips. It seems like with each update Ubuntu gets worse and worse and I think I could use some tidying up. But much of what I think I need to do isn't intuitive.

---

### Post by oldfred on 2012-07-23
I believe you should have a liveCD or repairCD for the current version of every system you have installed. So I suggest creating a new USB installer to have as a repairUSB. Check that you can use it to boot and then you have a way to repair if need be.

I also like to have other repair tools. I typically have gparted, Boot_repair, Super-grub and some other small distributions like Knoppix or Slitaz to boot with.
I like to have them all on one flash drive and maybe a separate CD so I can boot something.

The issue is often knowing what to do when it fails, but if you can boot liveCD, you can come to the forum and someone can help. :)

Mutli-boot ----------------------------------------------------------
These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

---

