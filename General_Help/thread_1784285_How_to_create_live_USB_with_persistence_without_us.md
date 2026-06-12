---
title: "How to create live USB with persistence without usb-creator?"
date: 2011-06-16
forum: General Help
---

### Post by Brushstroke on 2011-06-16
I've tried using usb-creator to create a persistent live USB of Ubuntu 10.04 32-bit, but the program is useless. There's a bug in the program that greys out the options to enable persistence ([see here for bug info]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/557775")). I tried workaround #4 listed in that link, but that didn't work either. When I selected another .iso which I moved to the /tmp directory as stated, the "Make Startup Disk" option then became greyed out as well. It'll make a bootable live USB but I need persistence. 

Is there a good way to do this without using that program, or can someone suggest a better program to use? And I tried Unetbootin twice, and it wouldn't boot the live system at all. After seeing the Ubuntu splash screen it just stalled at a black screen forever. 

Any options? 

Thanks.

---

### Post by C.S.Cameron on 2011-06-16
Following are methods for making persistent partitions using usb-creator and unetbootin. persistent partitions can be larger than 4GB.


usb-creator:

Booted Live CD.
Plugged in flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started "Create a live usb startup disk", (usb-creator).
Selected "Discard on shutdown".
Pressed "Make Startup Disk.
When usb-creator finished, ran "gksu nautilus"
Selected disk / syslinux / text.cfg and added "persistent" as shown:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, removed CD, rebooted.
Changed desktop background, connected to wireless and installed FontForge.
Rebooted, changes were persistent.


Unetbootin:

Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1GB FAT32 partition, (on the left side of the bar).
Created a 2GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext2 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Windows, started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, booted thumbdrive.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.

---

