---
title: "Can You Uinstall XP inside Ubuntu????"
date: 2009-10-05
forum: General Help
---

### Post by markene1 on 2009-10-05
Hi. I Just installed ubuntu. I was wondering if i could remove my old XP operative system. First i thought i would dual boot. But Ubuntu :guitar:. So i want to uinstall XP. Any help would be much aprisiated

---

### Post by justleen on 2009-10-05
you could simply delete/format the partition with gparted, and then remove the windows entry in grub.

---

### Post by Giblet5 on 2009-10-05
Your question is the opposite of the thread title.

Which do you want to do: install XP under Ubuntu or uninstall XP completely?

To install XP under Ubuntu, see VirtualBox, VMWare, Parallels, or any of the other virtualization systems.

To remove XP, reinstall Ubuntu and tell it to use the entire disk drive.

---

### Post by HiImTye on 2009-10-05
you can also boot from the live cd and use the partition editor to remove your windows partition and resize your ubuntu partition (if it is located on the same drive) - you *may* still lose all of your data though. dangers of playing with partitions

---

### Post by themusicalduck on 2009-10-05
Sometimes resizing partitions can take a long time, especially if you're moving a partition further up the drive to replace a deleted XP partition.

If you haven't installed much onto Ubuntu yet, you could just backup your home folder, then re-install and tell it to use entire disk like Giblet5 said.

---

### Post by markene1 on 2009-10-06
Hey Thanks for your fast answers. I have already set up ubuntu. Installed a bunch of programs. Started learning Python. So my question is how do i remove windows. Without reinstalling ubuntu. Thanks for your help. A great forum

---

### Post by oscarenzo on 2009-10-06
For install winXP inside ubuntu, you need install some software for virtualization, as: VMWARE or VIRTUALBOX.

Regards

---

### Post by zeroseven0183 on 2009-10-06
How did you install Ubuntu? Is it inside Windows (which is unlikely you'll do it because of your question, obviously) or side-by-side (different partition)?

---

### Post by joseinbaraj on 2009-10-06
if u have already uninstalled XP, try using Virtualbox.
It works perfect for XP and accessing various drives are very easy with Guest additions.

---

### Post by markene1 on 2009-10-06
> **zeroseven0183 said:**
> How did you install Ubuntu? Is it inside Windows (which is unlikely you'll do it because of your question, obviously) or side-by-side (different partition)?
I Created A Second Viritual Hardrive. And performed a clean install. I just want to get rid of xp. :P

---

### Post by justleen on 2009-10-06
Below are instructions for a "real" install, not a Wubi installation!!


find out what disk windows is installed on
```
 sudo fdisk -l | egrep 'NTFS|FAT32' 
```
this will return something like 
```
/dev/sdd3   *        6178        9216    24410767+   7  HPFS/NTFS 
```
install gparted if you haven't got it yet, and start it
```
 sudo apt-get install gparted
sudo gparted /dev/sdd

```
from there you should be able to select the NTFS drive and select "DELETE"

Once that is done all you have to do is remove the entry from grub 
```
 sudo update-grub
```

While your in gparted you might want to create a new partion with ext3/ext4 to get some extra space to use with  ubuntu.

---

### Post by markene1 on 2009-10-06
He He. Soon i almost go 1tb on ubuntu. A bit to much if you ask me :P

---

