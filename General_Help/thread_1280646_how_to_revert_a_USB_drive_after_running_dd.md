---
title: "how to revert a USB drive after running dd"
date: 2009-10-02
forum: General Help
---

### Post by frazerr on 2009-10-02
hi all

I am using my friends mac and USB to try to fix my netbook.

I need to fix my friends usb.

I ran
diskutil unmountDisk /dev/disk1
sudo dd if=/mini.iso of=/dev/disk1 bs=1m


the mini.iso did not work, but thats another story,
now I want to turn my friends USB back in to a portable drive.

at the moment it does not show up as a drive when I plug it in,
but it does show up if I run diskutil list

how do I format it back to a regular drive?

---

### Post by macabrem on 2009-10-02
> **frazerr said:**
> hi all

I am using my friends mac and USB to try to fix my netbook.

I need to fix my friends usb.

I ran
diskutil unmountDisk /dev/disk1
sudo dd if=/mini.iso of=/dev/disk1 bs=1m


the mini.iso did not work, but thats another story,
now I want to turn my friends USB back in to a portable drive.

at the moment it does not show up as a drive when I plug it in,
but it does show up if I run diskutil list

how do I format it back to a regular drive?

I don't have my Mac in front of me, but I believe that if you can see the drive in disk utility (the GUI version on the Mac), then you should be able to just click on it and choose an option in one of the menus to format it however you want it.

---

### Post by frazerr on 2009-10-02
> **macabrem said:**
> I don't have my Mac in front of me, but I believe that if you can see the drive in disk utility (the GUI version on the Mac), then you should be able to just click on it and choose an option in one of the menus to format it however you want it.
Thank you.

worked like a charm.

I just had to create a partition.

---

