---
title: "Is it possible to transfer contents of folders to a USB drive from command line?"
date: 2011-09-27
forum: General Help
---

### Post by maddbaron on 2011-09-27
I'm having difficulties accessing my gdm my fb ex is screwed up after I attempted to install gnome3  so I think I may have to reinstall my system but I'd like to know if it's possible to transfer the contents of certain folders into the USB drive as backup via command line?

---

### Post by Hakunka-Matata on 2011-09-27
Yes.
```
man cp
```

---

### Post by btindie on 2011-09-27
Of course.

When you connect your USB stick, type "dmesg | tail". That'll display the kernel messages that are generated as the device is initialised. What you're after is the sd* bit where it's something like sdb1 or sdc1, this is the partition number of your USB stick. Create a mount point "sudo mkdir /mnt/USB" then mount the parition "sudo mount /dev/sdc1 /mnt/USB" replacing "sdc1" with the partition as identified by the dmesg output. Then just use the cp command to copy the files to your USB stick. Finish it with "sync" then "sudo umount /mnt/USB".

---

### Post by maddbaron on 2011-09-27
I hate iPads autocorrect I typed fglrx and it said fb ex.... But thank u for the info.

---

