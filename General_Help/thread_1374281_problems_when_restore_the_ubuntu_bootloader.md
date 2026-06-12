---
title: "problems when restore the ubuntu bootloader"
date: 2010-01-06
forum: General Help
---

### Post by Forrestvt on 2010-01-06
Hi 
I have some problems to restore my bootloader for Unbuntu after I reinstalled the new win7 system on my dual boot computer. 

I boot my computer through the liveCD. Then:
sudo grub
find /boot/grub/stage1

I got Error 15: file not found.Then I try 
sudo chroot /mnt/root /bin/bash
I got: /bin/bash not such file or directory. Actually, I have this file in the directory. I am not sure what is wrong. 

Here are the results of fdisk -l
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       14593    76260555    f  W95 Ext'd (LBA)
/dev/sda5            5100       10198    40957686    7  HPFS/NTFS
/dev/sda6           10199       14593    35302806    7  HPFS/NTFS

I assume the win7 is in the sda1. 
Can some one give me some suggestions about what should i do?

---

### Post by cariboo on 2010-01-06
It doesn't look like you have Ubuntu installed the normal way. Are you using wubl?

---

### Post by Forrestvt on 2010-01-07
Here is how I installed the Ubuntu: 
I started the LiveCD under windows system. Then, installed the Ubuntu on a separated disk. The dual systems work fine. After that, I reinstalled the windows. Then, I lost the grub.
Is there anything wrong in what I did

---

