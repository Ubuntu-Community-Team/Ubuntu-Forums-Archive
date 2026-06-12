---
title: "User #1000 is locking me out of my files!"
date: 2011-02-23
forum: General Help
---

### Post by Rockcarver on 2011-02-23
Random files and folders have become locked, and when I try to open or copy them, I am informed that I am not the owner; user #1000 is the owner. How to get rid of user #1000??

I have been running 9.10 wubi; apparently Windows does not leave the Ubuntu files alone, resulting in a very unstable Ubuntu. Right now I am sorting out from a kernel panic and recovering data before reloading. 

Thinking wubi is not a good setup, maybe partitioning will be more stable.

---

### Post by mastablasta on 2011-02-23
> **Rockcarver said:**
>  
Thinking wubi is not a good setup, maybe partitioning will be more stable.
 
wubi sort of runs inside windows and within a large file :-)
 
it has it's number of issues. the can be overcome.
 
if you dont' have any important data in Wubi install it would be maybe better to uninstall it and do a side by side install to separate partition.

---

### Post by wiggly81 on 2011-02-23
you could also try installing ubuntu in virtualbox if the idea of changing partitions is daunting to you, this will provide you with a basic start point with no major changes to your system

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by Spyderkid on 2011-02-23
partioning is more stable

---

### Post by Rockcarver on 2011-02-23
Thanks, guys, for the advice on how to set up in the future. I downloaded the book, it has some good stuff in it that I didn't know before. 

But- any advice on how to unlock the locked files that are claimed by "user #1000" ?

Are there some terminal commands that will allow me to override the locked condition?

Rockcarver

---

### Post by Rockcarver on 2011-02-23
Oh, and 10.04: what is it by nickname? Is it more or less stable now? I am not a coder, and frequent crashes are not as amusing for me as they are for most of the visitors to the Forums.

 Especially when I am in the middle of a lecture and have to switch to Windows to show my slides, while the students wait restlessly :confused:

---

### Post by Stephen Morgan on 2011-02-23
```
sudo chown username filename
```  With username being your username and filename your filename. Or  ```
sudo chnod +r filename
```  User 1000 is "root".

---

### Post by oldfred on 2011-02-23
User 1000 is the default first user who also is the administrator. It should be you. Did you add another user or setup & boot into a second name.

This post discusses about uid (user) & gid (group) owenership.

Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

### Post by Rockcarver on 2011-02-23
Thanks, oldfred, I'll try those. Any idea why Ubuntu chose to randomly assign certain files to the root? I always sign in the same way, with my username, which I entered when I loaded the OS. Don't know any other way to log in. Have not established any other users.

Ubuntu is definitely not for my wife; too unstable and buggy. She would not be able to seek help in the Forums.

---

### Post by Morbius1 on 2011-02-23
This is bizarre.

Open a terminal and type:
```
id
```
What is your current uid?

---

### Post by Rockcarver on 2011-02-23
> **Morbius1 said:**
> This is bizarre.

Open a terminal and type:
```
id
```What is your current uid?

Morbius, thanks for the suggestion, but I cannot do this now. I have no findable kernel, Ubuntu does not run, except from the CD. I have been running Karmic in wubi, think I'll go to Lynx in a partition. If it happens again. I will try your suggestion.

Now I just need to get all my data out of root.disk. For that, maybe there is a terminal command that will allow me to override the lockup on the files.

Actually, I moved root.disk to an external drive, so I guess I can just go ahead and reload. But I have to figure out the partitions and what the boot procedure will be first.

---

### Post by Rockcarver on 2011-02-24
> **Stephen Morgan said:**
> ```
sudo chown username filename
```  With username being your username and filename your filename. Or  ```
sudo chnod +r filename
```  User 1000 is "root".

Had to go do other things for about a day. Tried to pry open a locked folder (OTHERP~1) with needed .jpgs in it, no luck. Any further advice? Here's what it looked like in terminal:

ubuntu@ubuntu:~$ sudo mkdir /win
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /win
ubuntu@ubuntu:~$ sudo mkdir /vdisk
ubuntu@ubuntu:~$ sudo mount -o loop /win/Ubuntu.Fixes/root.disk /vdisk
ubuntu@ubuntu:~$ id
uid=999(ubuntu) gid=999(ubuntu) groups=4(adm),20(dialout),24(cdrom),46(plugdev),105(lpadmin),119(admin),122(sambashare),999(ubuntu)
ubuntu@ubuntu:~$ sudo chown steve OTHERP~1
chown: invalid user: `steve'
ubuntu@ubuntu:~$ sudo chown 999 OTHERP~1
chown: cannot access `OTHERP~1': No such file or directory
ubuntu@ubuntu:~$ SUDO CHOWN 999 /win/Ubuntu.Fixes/root.disk/home/steve/OTHERP~1
SUDO: command not found
ubuntu@ubuntu:~$ sudo chown 999 /win/Ubuntu.Fixes/root.disk/home/steve/OTHERP~1
chown: cannot access `/win/Ubuntu.Fixes/root.disk/home/steve/OTHERP~1': Not a directory
ubuntu@ubuntu:~$ sudo chnod +r /win/Ubuntu.Fixes/root.disk/home/steve/OTHERP~1
sudo: chnod: command not found
ubuntu@ubuntu:~$ 


Thanks

Rockcarver

---

### Post by Vaphell on 2011-02-24
linux commands are case sensitive
sudo =/= SUDO
and at the end you had a typo with chnod (chmod)

can you go all the way to the directory in question with cd command? can you access it with nautilus?

---

### Post by bcbc on 2011-02-24
You're booting from the CD so you have no user 'steve' defined. You should have full access to all the files on the root.disk. 

You can use [ext2read]("http://ext2read.blogspot.com/") and view them from windows as well (just point it at the root.disk). If the root.disk has been corrupted run fsck on it (make sure you unmount it first).

```
sudo umount /vdisk
sudo fsck /win/Ubuntu.Fixes/root.disk
sudo mount -o loop /win/Ubuntu.Fixes/root.disk /vdisk
gksu nautilus /vdisk  #(browse and copy files)
```

---

### Post by Rockcarver on 2011-02-26
[SIZE=3][COLOR=Blue]Apologies for big gaps in the communications; I am teaching this weekend and get little time to run down the links you all have given me. Getting through them one by one.

Current status: root.disk had been squirreled away by windows; I found it and moved it to an external drive. The unlocked files in root.disk are safely in folders on the external drive. The locked ones are still a problem. I could not use Karmic, so uninstalled it. Still have XP as a backup. I am running Lucid from the lived CD till I figure out the details of partitioning. I ran fdisk -l with the following result:
[/COLOR][/SIZE]
[SIZE=2]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
129 heads, 4 sectors/track, 605778 cylinders
Units = cylinders of 516 * 512 = 264192 bytes
[/SIZE][SIZE=2]Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4592a56d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      198450    51200098    7  HPFS/NTFS
/dev/sda2          198451      605776   105090108    f  W95 Ext'd (LBA)
/dev/sda5          198451      605776   105090106    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS
ubuntu@ubuntu:~$ 


[SIZE=3][COLOR=Blue]sdb is my external drive. Any suggestions on partition modifications fo[/COLOR][/SIZE][/SIZE][SIZE=3][COLOR=Blue]r a dual boot of Lucid and XP in separate partitions? I don't have an easy way to reload XP, so would like to leave it more or less undisturbed.[/COLOR][/SIZE]

[SIZE=3][COLOR=Blue]Thanks, All.
rockcarver
[/COLOR][/SIZE]

---

### Post by gsgleason on 2011-02-26
> **Stephen Morgan said:**
> ```
sudo chown username filename
```  With username being your username and filename your filename. Or  ```
sudo chnod +r filename
```  User 1000 is "root".

No, it is not.  root is 0.

---

### Post by Rockcarver on 2011-02-28
> **bcbc said:**
> You're booting from the CD so you have no user 'steve' defined. You should have full access to all the files on the root.disk. 

You can use [ext2read]("http://ext2read.blogspot.com/") and view them from windows as well (just point it at the root.disk). If the root.disk has been corrupted run fsck on it (make sure you unmount it first).

```
sudo umount /vdisk
sudo fsck /win/Ubuntu.Fixes/root.disk
sudo mount -o loop /win/Ubuntu.Fixes/root.disk /vdisk
gksu nautilus /vdisk  #(browse and copy files)
```

[SIZE=3][COLOR=SeaGreen]Well, I ran this sequence above and it looked like it bombed: two pages of error messages. [COLOR=Red]BUT[/COLOR] I then had, as you said, full access to all the files in root.disk. So I cannot claim to remotely understand what happened, but Thanks to all, especially bcbc. This particular problem is solved. Now on the the next: How to partition for a dual boot from separate partitions.

Rockcarver[/COLOR][/SIZE]

---

