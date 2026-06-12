---
title: "Hard Drive Win XP install post Ubuntu Install"
date: 2011-08-31
forum: General Help
---

### Post by cheat117 on 2011-08-31
I had installed Natty Narwhal on my father-in-law's toshiba (New Seagate (I know) HDD after HDD failure). After using VMWare to install XP on his 1GB of ram he's decided to use XP as the primary. I've tried to install XP and the installer cannot find the hard drive after formatting the HDD as ntfs. Can anyone help?

---

### Post by oldfred on 2011-08-31
Windows need a primary partition formated NTFS with the boot flag or unallocated space so it can create one (and an available primary partition).

---

### Post by cheat117 on 2011-08-31
> **oldfred said:**
> Windows need a primary partition formated NTFS with the boot flag or unallocated space so it can create one (and an available primary partition).
 
I've done this, many times. I even unplugged the drive and formatted it in windows 7. 
 
Still no luck, I had grub rescue load after that then i cleaned it with spotmau partition magic, formatted it for ntfs, but how do i get it to have the boot flag

---

### Post by oldfred on 2011-08-31
In gparted it is right click on the partition, manage flags and choose boot. Only one boot flag per drive on a primary partition.
You can do it in Disk Utility or command line. 

set boot flag on for sda2 (off for others)
sudo sfdisk -A2 /dev/sda


Also in windows you set partition as active.

---

### Post by cheat117 on 2011-09-01
ill attempt that!

---

### Post by cheat117 on 2011-09-02
Setup still cannot find the hard drives. after being formatted as ntfs with boot flag. anyone else wanna take a stab at it?

---

