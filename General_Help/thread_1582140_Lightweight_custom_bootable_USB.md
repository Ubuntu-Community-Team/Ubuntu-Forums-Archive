---
title: "Lightweight custom bootable USB"
date: 2010-09-26
forum: General Help
---

### Post by gannggstaz on 2010-09-26
I want to make a bootable USB, prefferably Debian based. I want the barebones system, no GUI. Is there a way to make either a persistent boot (each sessions changes are saved to the USB) or preselect the packages before installing to USB?

---

### Post by Megaptera on 2010-09-26
Hi,
Is there anything at this link that might help? I've used the 'off-the-shelf' instructions but not tried what you're wanting to do ..
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by C.S.Cameron on 2010-09-26
For the 'buntus you can make an ext2, 3 or 4 partition named casper-rw that will save changes.

using usb-creator:

Boot Live CD.
Plug in flash drive.
Start Partition Editor
Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional)
Create a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk / syslinux / text.cfg and added "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.
You are persistent.

You can do similar with an UNetbootin install except:

Run "gksu nauilus", opened filesystem / cdrom and then open syslinux.cfg with text editor.
Add "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent

---

