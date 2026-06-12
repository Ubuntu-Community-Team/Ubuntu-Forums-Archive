---
title: "Boot problems - initramfs (Classic Issue)"
date: 2010-03-11
forum: General Help
---

### Post by mac666 on 2010-03-11
Hey 
I cant boot to Ubuntu 9.10 Karmic x64, havent change anything for months (Hardware or software)

I get the classic issue where you are sent to initframs to check /proc/cmdline - Which has correct UUID btw.

Im trying to boot on sda8.

```
ubuntu@ubuntu:~$ sudo blkid
**/dev/sda8: UUID="d473836c-7f32-4f08-a5e4-15d17a15ba44" TYPE="ext3" **SEC_TYPE="ext2" 
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="FCE68A53E68A0DD8" LABEL="Windows" TYPE="ntfs" 
/dev/sda5: UUID="21d1bbe5-92d4-46aa-aa7a-ad07dfd5c4bb" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="bbf6a965-0800-4b33-b117-dc5f56cc93e2" 
/dev/sda7: TYPE="swap" UUID="0a4eb6b1-d912-45d8-b3eb-9d388dc5ff30" 
/dev/sda9: TYPE="swap" UUID="f9b96f22-e54d-434e-834b-9b5104eea152"
```
```

ubuntu@ubuntu:~$ sudo fsck /dev/sda8
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda8: clean, 330865/9117696 files, 15200949/36443436 blocks (check in 3 mounts)
ubuntu@ubuntu:~$ 

```
/proc/cmdline UUID is correct

Anyone_?

---

### Post by mac666 on 2010-03-12
Please!!!! :(

---

### Post by mac666 on 2010-03-13
Since noone help this is what i had to do,

Since everything was in order but the computer just would boot, it couldnint find my partion  where it was suppose to boot from, i ran ubuntu from live cd and Removed a swap partion, and resized my ubuntu partion, then i got Grub error 22, so i reinstalled Karmic on another partion to get grub to refresh, then everything worked!!

---

