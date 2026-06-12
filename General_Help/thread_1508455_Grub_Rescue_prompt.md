---
title: "Grub Rescue prompt"
date: 2010-06-13
forum: General Help
---

### Post by GirishSharma on 2010-06-13
Hello Friends,
 
yesterday i was running badblocks command; to fix 1 bad block in my HDD... this command worked for 10 minutes; then screen became black out; no message nothing; only mouse pointer was there... i waited another 5 minutes... still nothing was there... (how much i could wait.. so i switched off the computer);; when i switched on ... it is saying "Unkonwn file system" and one grub rescue> prompt is there... Its Ubuntu 10.04 on p4 32 bit machine.
 
At this prompt i am not able to do anything; it says "Unnown command". I have all tried with even installation cd; in terminal
 
1.linux rescue : it is saying to install a package or something else
2.chroot /mnt/sysimage : it is saying no such file or directory etc.
3.fsck : The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains on ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock.
4. etc. etc.
5. Different forum reading... no result..
 
Kindly help me, i do'nt want to reinstall; untill and unless some expert do'nt say "Its impossible to recover in your case".
 
Regards
Girish Sharma

---

### Post by dcstar on 2010-06-13
> **GirishSharma said:**
> Hello Friends,
 
yesterday i was running badblocks command; to fix 1 bad block in my HDD... this command worked for 10 minutes; then screen became black out; no message nothing; only mouse pointer was there... i waited another 5 minutes... still nothing was there... (how much i could wait.. so i switched off the computer);; when i switched on ... it is saying "Unkonwn file system" and one grub rescue> prompt is there... Its Ubuntu 10.04 on p4 32 bit machine.
 
At this prompt i am not able to do anything; it says "Unnown command". I have all tried with even installation cd; in terminal
 
1.linux rescue : it is saying to install a package or something else
2.chroot /mnt/sysimage : it is saying no such file or directory etc.
3.fsck : The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains on ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock.
4. etc. etc.
5. Different forum reading... no result..
 
Kindly help me, i do'nt want to reinstall; untill and unless some expert do'nt say "Its impossible to recover in your case".
 
Regards
Girish Sharma

Search for instructions on using a Live CD to run fsck.

---

### Post by GirishSharma on 2010-06-13
3.fsck : The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains on ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock.
 
I have tried fsck with sudo fsck /dev/sda1 it returned above message.  When i says :
sudo e2fsck -b 8193 /dev/sda is says :
Device or resource busy while try to open /dev/sda.  Filesystem mounted or opened exclusively by another probram?
 
Regards
Girish Sharma

---

### Post by GirishSharma on 2010-06-13
When i checked with :
# sudo e2fsck /dev/sda1
e2fsck: 1.41.11 (14-Mar-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad image number in super-block while  trying to open /dev/sda1
 
Same error when i says
# sudo e2fsck -b 8193 /dev/sda1
 
Any update please.
 
Thanks and Regards
Girish Sharma

---

