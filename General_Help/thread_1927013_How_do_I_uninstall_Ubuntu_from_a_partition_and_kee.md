---
title: "How do I uninstall Ubuntu from a partition and keep grub?"
date: 2012-02-17
forum: General Help
---

### Post by kimharding on 2012-02-17
I have two versions of Ubuntu on two different partitions, I now want to remove one while keeping the other. I can find plenty of instructions for removing Ubuntu but these also remove Grub, which would mean I couldn't boot into the remaining version. So how do I uninstall Ubuntu from a partition and keep grub?

---

### Post by drs305 on 2012-02-17
Boot into the Ubuntu you want to keep. Make sure it is the controlling Grub:
```
sudo grub-install /dev/sda  # Assumes the OS is on sda, if not change the command
sudo update-grub

```
This will point the sda MBR to your current Grub files.

Uninstalling Ubuntu should not affect your MBR. It will remove the Grub files from the undesired Ubuntu partition, but these files are not used if you have run the command above from the OS you want to keep.

If for some reason you can't boot after uninstalling, boot a LiveCD (same version as the OS you are keeping), mount its partition, and run the following commands. X is the drive letter, Y is the partition number. Don't include the partition in the second command.
```
sudo mount /dev/sdXY /mnt # Example sda5
sudo grub-install --root-directory=/mnt /dev/sdX # Example sda
```

---

### Post by kimharding on 2012-02-17
Thanks, did that and Grub behaved just fine.

The only problem was that start up stalled. This was due to a problem with the fstab file having the wrong UUID for the partition which I formatted to remove the other copy of Ubuntu. So had to edit this from a live CD. Anyway, it is working now.

---

