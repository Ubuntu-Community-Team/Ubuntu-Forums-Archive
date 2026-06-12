---
title: "fsck checks partition which doesn't exist"
date: 2009-11-15
forum: General Help
---

### Post by zedi on 2009-11-15
I tried beginers forum but nobody answered my call for help.
I can't boot to Jaunty after I installed Karmic. Quote from /var/log/fsck/checkfs: 

“  fsck.ext3: Unable to resolve 'UUID=3769aaaa-269d-4d78-aee4-7ba71e8f7fe6'     fsck died with exit status 8.” 

That's very veird because, there isn't such thing like partition 'UUID=3769aaaa-269d-4d78-aee4-7ba71e8f7fe6' .

Bellow, the result of command sudo blkid :
 
/dev/sda1: UUID="4AB5-62A3" TYPE="vfat" 
/dev/sda2: UUID="4AB5-674F" TYPE="vfat" 
/dev/sda3: UUID="8bd9d260-04ff-439f-a29d-be2bc7aab992" TYPE="ext3" 
/dev/sdb1: UUID="b49cd7d9-dcea-466b-b35d-51b2f0853d5d" TYPE="ext4" 
/dev/sdb2: UUID="c85b1e91-60e6-468a-b511-c9d9baa58183" TYPE="ext3" 
/dev/sdb5: UUID="120babd8-22b5-4b9a-97b4-d6a11706b838" TYPE="ext3" 
/dev/sdb6: UUID="f13168b3-cb86-469f-ae3d-c811a8c9b57f" TYPE="swap" 
/dev/sdb7: LABEL="WinPage" UUID="AE23-C13C" TYPE="vfat"

My partitions are &#8594;  /dev/sdb1: Karmic, /dev/sdb2: Jaunty, /dev/sdb5: /home. The first disk - /dev/sda is for Winblows & store.

Normal booting to Jaunty gives just black screen with flashing cursor -. In Recovery mode -  the message like above.
What bloody fsck is trying to check and what I can do to fix it?

---

### Post by grandtoubab on 2009-11-15
check your /etc/fstab

sudo fdisk -l
sudo cat /etc/fstab

---

### Post by zedi on 2009-11-17
grandtoubab,
                      
                      SPOT ON! So simple, just 1 line (karmic) in fstab wrong – that's all.
I'm writing this from Jaunty and its fixed!!!
Thank you very much, I really appreciate – viva la France!

zedi

---

