---
title: "Repairing Buffer I/O errors using fsck"
date: 2006-04-28
forum: General Help
---

### Post by dglp on 2006-04-28
My machine has just produced two buffer I/O errors on startup, and suggests that I run fsck manually. I'm not sure what this entails, and am first wondering if fsck is a repair utility. I have tried rebooting, have succesfully started from the Live CD, so I gather it's not a hardware problem in the broad sense. The error comes up again when I boot from the hard drive. 

The errors refer to hda2, my Linux partition: 
4294712.744000 Buffer I/O error on device hda2, logical block 22672115.0% 
4294721.585000 Buffer I/O error on device hda2, logical block 226721 
Error reading block 226721 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 95172 
Unexpected inconsistency; run fsck manually. 

I've looked at this Man page explanation, but am none the wiser for it: [http://www.linuxmanpages.com/man8/fsck.8.php]("http://www.linuxmanpages.com/man8/fsck.8.php") 

A few minutes later... 
Having taken a wild guess, I have run 1) umount /dev/hda2, and 2) fsck /dev/hda2, and part-way through, get a reference to the error, which asks if I should ignore it. I answered Yes, then forced a rewrite, and fixed the error. It carries on through checking directory structure up to Pass 5 then asks if A block bitmap difference should be fixed. Again, Yes, and so on through other requests. It ends by giving a File System Was Modified message and asks to reboot. 

That seems to have done the trick.

---

### Post by thesandeep on 2006-10-14
I too got the same problem. But am getting Ubuntu installed but wile it is booting in the phase chcking filesystems its facing the problm

I/O Error while reading to the logical drive /dev/sda1 in logical block 103432539.[43959]

I used to face this once ...but i thought it was a problem with my HDD but even with my new HDD I am facing this problem. But when i ahave installed Ubuntu LTS 6.06 on my system i got no problem but ..recently (2 weeks after installation) i got once again this problem

---

### Post by lpvdes on 2006-10-18
I allready had 2 PC's that gave me the I/O error and one that had grub corrupted. Do you think there is a bug in the Ubuntu distribution.

---

### Post by thesandeep on 2006-10-21
I suggest you to remove that default file system check from your /etc/init.d/ so this will avoid the automatic filesystem check. To do that use Live CD and go ahed like this 

$sudo su -
#mount /device(root partition) /mountpoint
(if you are not aware of devices issue this command 
#fdisk -l
this will show all the partitions on your system)
#chroot /mountpoint
#update-rc.d -f checkfs.sh remove
..........
#reboot

I faced the same I/O error problem in this file system check so i did this but i regulary ckeck my file systems mannually

---

