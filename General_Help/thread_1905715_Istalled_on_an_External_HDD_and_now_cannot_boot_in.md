---
title: "Istalled on an External HDD and now cannot boot into Windows"
date: 2012-01-07
forum: General Help
---

### Post by tombombodil on 2012-01-07
Hello, I just recently purchased and external HDD with the intent if installing Ubuntu 11.10 on it.

I used my laptop as the interface. I booted from a USB drive and completed the installation process choosing "delete and install". I selected the External HDD and it said it would delete the existing partitions which was fine as it was fresh out of the box.

I completed the installation process and it promted me to reboot. I did. This is when all the problems started.

The bios freezes/is extremely slow on startup if the External HDD is connected (via USB 3.0 cable). Also it does not always show up as a bootable device. 

When it does and I select it it does not boot, it does not even enter a grub recover, it just sits with a single blinking cursor at the top left corner of the page.

Also now when I try to boot into windows from the laptops internal HDD I something like this: "error no such device" and then a "grub recover" terminal.

When I try to restore Grub through this interface a lot of the commands don't get any response, not even an error message, it just goes to the next line with the same promt: "grub recover" with no sub text.

I am at a complete loss.

Any and all help would be appreciated.

---

### Post by imachavel on 2012-01-07
remove the hdd. reboot the machine. now when you reboot the machine, the blinking cursor goes away right? does your main os boot from grub? if it does, reconnect the drive, try and reboot. if the external hdd boots then great! If not boot back into your main OS partition. Now that you have accomplished this, try reformatting the drive and reinstalling the OS one more time on the external hdd. 

If you remove the drive, reboot and you can't boot into your main OS partition on main internal hdd, then put the linux live cd into the drive, reboot and select the linux live cd to boot into, and try and find recovery options in the terminal.

if you don't know them, revisit this thread, once you have booted to the live cd, and ask away in the forums. I'm not great with linux recovery, I'm actually just learning!

---

### Post by tombombodil on 2012-01-07
My primary os (Windows 7) will not boot, if I reboot with the External HDD detached I get the error "no such device" and a grub recover line.

I'm going to go ahead and try to reinstall Ubuntu to the External HDD.

Also when I boot from the USB drive, I can see the primary HDD and all of the files and registries appear intact. So I don't know why it wouldn't boot.

I'll update after the install.

---

### Post by imachavel on 2012-01-07
wait a minute, if you can't boot to the primary drive and primary OS partition, then how in the world are you going to reinstall the OS to the external hard drive? I'm confused. Can you see the primary hard drive in the list of bootable devices when you chose what device to boot into to at the bios? Did you mount the external hard drive when you installed the OS to it? If you copied the files, the boot sectors will not copy over, I'm going to explain why in a minute, as I have a similar(but not the same issue)

---

### Post by oldfred on 2012-01-07
On any of the auto install options grub automatically installs to sda, or usually the first internal drive. You need to install grub to sdb, the external and restore the Windows boot loader or a work alike to sda.

Complete instructions here:
Boot Problems:Computer does not boot without external drive
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

### Post by tombombodil on 2012-01-07
I have a 2 bootable Flash Drives, one for Ubuntu and one Windows 7. So I was going to install from those.

When I enter the boot menu the BIOS sees the following devices: "Internal Netbook HDD" and DVD Drive. When I select the internal netbook HDD I get the aforementioned error.

I didn't copy any files. What I meant is that when I boot into Ubuntu from the LiveCD Image on the Flash Drive, I can see both drives the External and the Primary and all of the files, personal and system, are intact. So I am unsure as to why I can't boot from them.

The only things that I can boot from or that the BIOS can see as bootable devices with any consistency are the bootable Flash Drives.

---

### Post by efflandt on 2012-01-07
When you reinstall, do not do automatic partitioning, that is what may have gotten you into this situation. At the partitioning part of install select **Other**, pick the partition(s) on external drive for / and swap [or remove them and set up partition(s) you want] , and pay attention to the drop down list at the bottom of that partitioning screen to install grub to the external drive (/dev/sdb?).

Then fix the Windows mbr from Ubuntu with:

```
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```which works from a running Ubuntu system, and I imagine is also available if running a live system on install CD or bootable iso on USB.

---

### Post by tombombodil on 2012-01-07
Ok I'm starting to get a bigger picture.

From the installation partitioner I can see in the list of devices the partition with the Windows  7 loader and the Linux loader. From the BIOS (and I haven't pinned down exactly how I did it) I've managed to access a purple screen with white text that lists all of the bootable partitions in a much different format than the BIOS boot order utility. It lists the OS mentions a "loader" in parentheses along with some other relevant info. 

From this menu I can boot into both my primary OS (Window 7) and the Ubuntu on the external hdd. So I can boot from this menu but not from the BIOS menu that you access by hitting a function key on start up.

I've only accessed this seperate menu twice both times by hitting random startup relevant keys at just the right time, not sure exactly what.

So the devices are bootable the BIOS just doesn't know how to mount/boot from them.

Any of this ring any bells?

---

### Post by tombombodil on 2012-01-07
> **efflandt said:**
> When you reinstall, do not do automatic partitioning, that is what may have gotten you into this situation. At the partitioning part of install select **Other**, pick the partition(s) on external drive for / and swap [or remove them and set up partition(s) you want] , and pay attention to the drop down list at the bottom of that partitioning screen to install grub to the external drive (/dev/sdb?).

Then fix the Windows mbr from Ubuntu with:

```
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```which works from a running Ubuntu system, and I imagine is also available if running a live system on install CD or bootable iso on USB.

+1

This fixed the problem. Thanks for all your help guys. It's awesome that there is such a great support community for this :).

---

### Post by imachavel on 2012-01-07
the bios isn't necessary to access to access either partition in dual boot, only to select a drive if you have more then one drive installed(for example external hard drive)

as you said, dual booting only requires two partitions, now that you see them both, you can select either one? I'm assuming this thread is solved? mark as so please so when people google this problem they can follow instructions step by step :P

---

### Post by imachavel on 2012-01-07
> **efflandt said:**
> When you reinstall, do not do automatic partitioning, that is what may have gotten you into this situation. At the partitioning part of install select **Other**, pick the partition(s) on external drive for / and swap [or remove them and set up partition(s) you want] , and pay attention to the drop down list at the bottom of that partitioning screen to install grub to the external drive (/dev/sdb?).

Then fix the Windows mbr from Ubuntu with:

```
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```which works from a running Ubuntu system, and I imagine is also available if running a live system on install CD or bootable iso on USB.

I had this same problem and wish I would have known this command back then, but since I'm not dual booting windows, this is my synax, I'll have to pay careful attention to remember this:

0+1 records in
0+1 records out
440 bytes (440 B) copied, 0.0056639 s, 77.7 kB/s

any links that point out these exact same steps as:

sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

---

