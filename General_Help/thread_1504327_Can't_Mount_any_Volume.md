---
title: "Can't Mount any Volume"
date: 2010-06-07
forum: General Help
---

### Post by mamamia88 on 2010-06-07
I keep getting this error message.  i don't want to go back to windows but if I can't fix this I'm afraid I will have to so I can listen to my podcasts.  Does anyone know how to fix this error?

---

### Post by WorMzy on 2010-06-07
That's an odd message. Have you modified /etc/fstab?

Try manually mounting the partitions you want. The following command, when entered into a terminal, will tell you which partitions your system knows about:
```
sudo blkid
```
Once you know (or have an idea about) which one you want to mount, create a directory for it to be mounted into with:
```
sudo mkdir /media/FOLDERNAME
``` Then mount the partition there with the following command: ```
sudo mount -t ntfs /dev/sda1 /media/FOLDERNAME
```

PLEASE NOTE: Only use the "ntfs" statement in the above command for ntfs partitions, switch it with ext4, vfat, etc, as necessary.

---

### Post by mamamia88 on 2010-06-07
this is output not sure what to really do after first step /dev/sda1: UUID="ca8b7966-40e7-447e-8330-87a7d1f831fa" TYPE="swap" 
/dev/sda2: UUID="cb689562-de6c-4415-b9ff-431ea653fe0d" TYPE="ext4" 
/dev/sda5: UUID="9d66a908-936c-4a85-a776-ada68078b547" TYPE="ext4" 
/dev/sdb: UUID="0123-4567" TYPE="vfat" 
sportscrazed2@shawnsroom-laptop:~$ sudo mkdir /media/FOLDERNAME
mkdir: cannot create directory `/media/FOLDERNAME': No such file or directory
sportscrazed2@shawnsroom-laptop:~$ sudo mkdir /dev/sdb/mountfolder
mkdir: cannot create directory `/dev/sdb/mountfolder': Not a directory
sportscrazed2@shawnsroom-laptop:~$ sudo mkdir /media/FOLDERNAME
mkdir: cannot create directory `/media/FOLDERNAME': No such file or directory
sportscrazed2@shawnsroom-laptop:~$ sudo mount -t vfat /devsdb /media/FOLDERNAME
mount: mount point /media/FOLDERNAME does not exist
sportscrazed2@shawnsroom-laptop:~$

---

### Post by WorMzy on 2010-06-07
> /dev/sda1: UUID="ca8b7966-40e7-447e-8330-87a7d1f831fa" TYPE="swap"
/dev/sda2: UUID="cb689562-de6c-4415-b9ff-431ea653fe0d" TYPE="ext4"
/dev/sda5: UUID="9d66a908-936c-4a85-a776-ada68078b547" TYPE="ext4"
/dev/sdb: UUID="0123-4567" TYPE="vfat"

This tells us that you have four partitions that the system knows about. It looks like one hard drive with three partitions, and a USB flash drive (possibly, I'd expect a number to be after the "sdb")

> sportscrazed2@shawnsroom-laptop:~$ sudo mkdir /media/FOLDERNAME
mkdir: cannot create directory `/media/FOLDERNAME': No such file or directory

That, I fear, is the root of your problem. Can you open a terminal, run "ls /", and post the output here. It looks like you don't have a /media folder, which would be why you can't mount.

---

### Post by mamamia88 on 2010-06-07
bin    etc             lib         mnt   sbin     tmp      vmlinuz.old
boot   home            lib32       opt   selinux  usr
cdrom  initrd.img      lib64       proc  srv      var
dev    initrd.img.old  lost+found  root  sys      vmlinuz

---

### Post by WorMzy on 2010-06-07
Aye, I was right, you're missing /media. Run "sudo mkdir /media" and it should fix all your mounting problems. You'll be able to mount them from Nautilus, like you were initially trying to, you won't need to do it manually.

---

### Post by FuturePilot on 2010-06-07
> **mamamia88 said:**
> bin    etc             lib         mnt   sbin     tmp      vmlinuz.old
boot   home            lib32       opt   selinux  usr
cdrom  initrd.img      lib64       proc  srv      var
dev    initrd.img.old  lost+found  root  sys      vmlinuz

You're missing /media.
```
sudo mkdir /media
```

You shouldn't have to do anything else. Just plug it in and it should automatically mount.

---

### Post by mamamia88 on 2010-06-07
omg i fixed it. thanks alot guys.  any idea what could have happened to make this important file dissapear?

---

### Post by FuturePilot on 2010-06-07
> **mamamia88 said:**
> omg i fixed it. thanks alot guys.  any idea what could have happened to make this important file dissapear?

Were you running any commands before this broke? Or maybe running Nautilus as root and deleting files?

---

### Post by WorMzy on 2010-06-07
You must have accidentally removed it at some point. By default, it can't be removed without a sudo command.

---

### Post by mamamia88 on 2010-06-07
actually i was running nautilus as root to delete a few nautilus scripts for mounting isos.  must have accidently deleted it

---

