---
title: "Trouble with mounting an external hard drive, possibly caused by NTFS Config"
date: 2012-01-31
forum: General Help
---

### Post by ttimm68 on 2012-01-31
I bought a Toshiba 500 GB external hard drive about a month ago and I am having trouble with mounting. I installed NTFS Config, not due to problems with this drive, but to automatically mount my windows partition, as I have successfully done previously. I accidently set the program to mount my External drive and now the program takes ownership of the drive in a way. The drive now has to be connected to the computer or the computer will not boot up (into Xubuntu) and will just say waiting to mount drives until I plug it in. Once I am up and running if I unplug the drive and plug it back in it will not mount and will say you do not have permission to mount the drive. I have tried uninstalling NTFS Config, but that doesn't fix the problem. I hope someone can give me the freedom to use this drive on Xubuntu without this NTFS Config nonsense.

---

### Post by oldfred on 2012-02-01
NTFS config added an entry to fstab.

Post fstab if you have a question or this would back it up & let you edit it:

# Find your UUID:
sudo blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to:
sudo mount -a

---

