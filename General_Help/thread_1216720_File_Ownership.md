---
title: "File Ownership"
date: 2009-07-18
forum: General Help
---

### Post by zaidqais on 2009-07-18
Hi guys
I have a problem with changing the ownership of file ("max.doc") to the user max
 
[COLOR=#000000][COLOR=#0000bb]```
 
[COLOR=#000000][COLOR=#0000bb]zaid[/COLOR][COLOR=#007700]@[/COLOR][COLOR=#0000bb]zaid[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]desktop[/COLOR][COLOR=#007700]:/[/COLOR][COLOR=#0000bb]media[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]GAMES[/COLOR][COLOR=#007700]$ [/COLOR][COLOR=#0000bb]chown max max[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]doc
chown[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000bb]changing ownership of [/COLOR][COLOR=#007700]`[/COLOR][COLOR=#0000bb]max.doc': Operation not permitted
zaid@zaid-desktop:/media/GAMES$ sudo chown max max.doc
chown: changing ownership of [/COLOR][COLOR=#007700]`[/COLOR][COLOR=#0000bb]max[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]doc[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000bb]Operation not permitted
zaid[/COLOR][COLOR=#007700]@[/COLOR][COLOR=#0000bb]zaid[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]desktop[/COLOR][COLOR=#007700]:/[/COLOR][COLOR=#0000bb]media[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]GAMES[/COLOR][COLOR=#007700]$ [/COLOR][/COLOR]

```
 
[COLOR=black]i tried using sudo by there no use , hopefully you can help me  :D[/COLOR]
[COLOR=#000000][/COLOR] 
[COLOR=#000000]Thank you[/COLOR]
[/COLOR][/COLOR]

---

### Post by aysiu on 2009-07-18
What filesystem is /media/GAMES?

NTFS? FAT32? HFS+?

---

### Post by michy99 on 2009-07-18
When you tried sudo did it ask for your password?

---

### Post by SuperSonic4 on 2009-07-18
With chown it's usually ```
sudo chown user:group /path/to/file
```

often user and group are one an the same, such as sonic:sonic in my case

---

### Post by zaidqais on 2009-07-18
>  
When you tried sudo did it ask for your password? 

yes , it asked but i didnt put it in my first post
>  
What filesystem is /media/GAMES?
NTFS? FAT32? HFS+? 

FAT32

---

### Post by merlinus on 2009-07-18
IIRC, you cannot use linux permissions on fat32 files and partitions.

What you can do, however, is to run nautilus as root, navigate to the file, rightclick, properties, permissions, and see what you can do.

```
gksu nautilus
```

---

### Post by michy99 on 2009-07-18
FAT32 filesystems do not support linux permissions. The permissions are determined when the partiton is mounted. Are you mounting the partition automatically at boot with fstab? If so, you probably need to make changes to fstab. What do you get for these commands? ```
ls -l /media
cat /ect/fstab
sudo fdisk -l
```

---

### Post by zaidqais on 2009-07-18
Thank you guys , Now I know what the cause is :-)
I am still a newbie in linux , so it is enough for me now ...
 
Thank you

---

