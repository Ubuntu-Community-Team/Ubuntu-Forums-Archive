---
title: "How To change permission folder so only root can open it"
date: 2011-04-18
forum: General Help
---

### Post by Matadewa on 2011-04-18
hi All. . . 
same as title of this thread. . . 
i wonder how to change permission folder, so only root can open it?

---

### Post by thecamelcoder on 2011-04-18
You'll need to use the following commands.

1. Change the ownership of the directory / file to root
chown root:root <path-to-dir>

2. Change the permissions so that only the owner of the file can read/write/execute it
chmod 700 <path-to-dir>


And your done!

):P

---

### Post by Matadewa on 2011-04-18
> **thecamelcoder said:**
> You'll need to use the following commands.

1. Change the ownership of the directory / file to root
chown root:root <path-to-dir>

2. Change the permissions so that only the owner of the file can read/write/execute it
chmod 700 <path-to-dir>


And your done!

):P

 hai thanks for answer 
but i still can access the folder without become root 
this is what i wrote in terminal  
( fileFolder is a name of my folder which i wants to lock ) 
-> **chown root:root fileFolder **
-> **chmod 700 fileFolder  **
and when i type ls -l in terminal 
**drwxrwxrwx 1 root root 0 2011-04-18 16:54 fileFolder  **where is my mistake :D

---

### Post by Karlchen on 2011-04-18
Hello, Matadewa.

The folder named **fileFolder** is owned by **root**. Therefore only **root** can change its properties. Haha, this would be a nice security breach if anybody were permitted to change the properties of root's objects. ;)

Therefore you will have to run the chmod commandline like this: ```
sudo chmod 700 fileFolder
```HTH,
Karl

---

### Post by kiyop on 2011-04-18
> **Matadewa said:**
> when i type ls -l in terminal drwxrwxrwx 1 root root 0 2011-04-18 16:54 fileFolder

For ext2/3/4 filesysytems, "sudo chown" and "sudo chmod" is effective.

But, for FAT32, or NTFS filesystem, and so on, you cannot change owner and partition individually.

Edit:> The above "partition" is wrong. "permission" is right.

You can set owner and permission for all the files (and all the directories) in the partition by mount option, such as "uid=...", "umask=..." and so on.

What is the filesystem of the partition which involves the directory to which you want to deny access from ordinary user?

---

### Post by Matadewa on 2011-04-18
**[B]@**[/B][Karlchen ]("http://ubuntuforums.org/member.php?u=1256016")
Hello Karichen thanks for your answer. . . 
i really forget about that, no doubt it's will be nice security :D
but it's give no effect, i still can access it without become root 

@[kiyop]("http://ubuntuforums.org/member.php?u=1246530")
hai Kiyop thanks for your answer, it's really helped me
when i try in /home directory (ext4) it's work, actually it's enough for me
because my important file have small size so i can save it in /home directory
but i wonder how to do same in ntfs or fat32 partition?  :D

---

### Post by Karlchen on 2011-04-18
Hello, Matadewa.

As kiyop correctly pointed out: > But, for FAT32, or NTFS filesystem, and so on, you cannot change owner and partition individually.
You can set owner and permission for all the files (and all the  directories) in the partition by mount option, such as "uid=...",  "umask=..." and so on.So you will have to modify the mount options for your NTFS and FAT32 partitions appropriately. The commands chown and chmod will be of no use on FAT32 and NTFS partitions.

Kind regards,
Karl

---

### Post by kiyop on 2011-04-18
> **Matadewa said:**
> i wonder how to do same in ntfs or fat32 partition?  :D
On linux including Ubuntu, you need to give correct mount option in order to configure owner and permission to files in NTFS or FAT32 partition.
Please refer to:
```
man mount
```and find "uid", "gid", "umask" section in "ntfs" and "fat".

---

### Post by Spyderkid on 2011-04-18
_use this to make your folder root access only...._
***sudo chmod 700 fileFolder***


_then to open a root nautilus file manager use this..._
***sudo nautilus***

---

### Post by Matadewa on 2011-04-18
> **kiyop said:**
> On linux including Ubuntu, you need to give correct mount option in order to configure owner and permission to files in NTFS or FAT32 partition.
Please refer to:
```
man mount
```and find "uid", "gid", "umask" section in "ntfs" and "fat".

I still didn't understand well
where i can find "uid", "gid", "umask" section in "ntfs" and "fat"
i just set this in fstab for automount my partition 
```
"uid", "gid", "umask" section in "ntfs" and "fat" 
```
:D

---

### Post by Matadewa on 2011-04-18
@[Karlchen]("http://ubuntuforums.org/member.php?u=1256016")
he. . . he
you have same opinion as me :D
but as i say, actually i can save my important file in /home directory because my file have small size
i just wonder how to do same in ntfs or fat32
by the way thanks for you advice :D

[@Spyderkid]("http://ubuntuforums.org/member.php?u=1191200")
thanks for your advice. . .
but it's seem didn't work in ntfs or fat32 partition my friend :D

> **kiyop said:**
> On linux including Ubuntu, you need to give correct mount option in order to configure owner and permission to files in NTFS or FAT32 partition.
Please refer to:
```
man mount
```and find "uid", "gid", "umask" section in "ntfs" and "fat".

I still didn't understand well
where i can find "uid", "gid", "umask" section in "ntfs" and "fat"
i just set this in fstab for automount my partition 
```
 /dev/sda4 /media/Tantra ntfs-3g default,locale=en_US,utf8 0    0 
```:D
is that wrong?

---

### Post by Morbius1 on 2011-04-18
Assuming you already created /media/Tantra and that it is in fact an ntfs partition then just add umask=077 to the list of options:
 ```
/dev/sda4 /media/Tantra ntfs-3g default,umask=077,locale=en_US,utf8 0    0
```Then run the following command to test for errors ( and post them if you get errors ) and mount the partition:
```
sudo mount -a
```If it does error then post the output of the following commands:
```
sudo blkid -c /dev/null
cat /etc/fstab
mount
```

---

### Post by kiyop on 2011-04-18
I am not familiar with NTFS, to tell the truth.

How about adding ",umask=077,uid=0,gid=0" just after "utf8"?

I will do by myself and check if it works or not.

Edit:
Thanks Morbius1.
I did not notice that you had posted #12 when I first submitted the above (#13).
Options "uid=0" and "gid=0" may be default, and so are not necessary.
I confirmed on Ubuntu 10.10.

---

### Post by Matadewa on 2011-04-18
@[kiyop]("http://ubuntuforums.org/member.php?u=1246530") @[Morbius1]("http://ubuntuforums.org/member.php?u=982144")
i finished edit configure /etc/fstab and mount it successfully
but it's seem not give any chance when i try to sudo chmod 700 fileFolder ( fileFolder already by root and group root)
am you success to change permission in ntfs? :D

---

### Post by Morbius1 on 2011-04-18
You can not change ownership ( chown ) or permissions ( chmod ) of a Windows filesystem ( NTFS FAT32 ) after it's mounted. 

You can only change those things at the moment of mount - as you have done in fstab. And it only has that property while it's mounted. This is just the opposite of a Linux filesystem.

Also unlike Linux filesystems the individual files and folders withing the NTFS partition inherit the ownership and permissions of the partition itself. You cannot as has been stated earlier change the ownership or permissions of individual files and folders.

Right now all folders within /media/Tantra will have owner = root and permissions of 700 - every single one of them.

---

### Post by Matadewa on 2011-04-19
owh i see
so it's why my partition not otomaticaly mounted when i restart
and i must become root to mount that partition
really thanks. . .i'm more understand now about permission :D

---

