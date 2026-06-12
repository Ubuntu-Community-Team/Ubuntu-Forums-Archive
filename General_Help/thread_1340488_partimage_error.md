---
title: "partimage error"
date: 2009-11-28
forum: General Help
---

### Post by xieu90 on 2009-11-28
hi,
i installed ubuntu with ext4 file system
today i wanted to clone/backup it with partimage from rescuecd, so if anything happen i dont have to reinstall everything

i use rescuecd almost every month so i dont think i made any mistake
but i got this message:
can't read bitmap block 0 from image

then i tried to save another image from xp, and it ran,
so what would the problem be?
could it be that rescuecd(or rather the partimage in rescuecd) doesnt support ext4 file system ?

how can i solve that problem then ?

---

### Post by mechro on 2009-11-28
ext4 not supported in partimage...

[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

### Post by mechro on 2009-11-28
Gparted can copy partitions and it supports ext4. There is a Linux LiveCD called Parted Magic which includes Gparted and other rescue tools...

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by jbrown96 on 2009-11-28
I'm not familiar with that software, so it's possible that it doesn't support ext4. I would say that it's more likely that it's having problems with a bad block. I wouldn't recommend running backups this way. Copying at the block level is very expensive (in time) and can silently copy errors. You are much better off using something like rsync. 

Rsync is really good because it will only copy what is necessary. It's not any faster when all the data has changed (first backup), but monthly updates don't ususally have large changes in data, so they go much faster. 

Here's a basic rsync command ```
rsync -avz /SOURCE/PATH/ /DESITNATION/PATH
``` 
There is a trick with the way that you type the source path. The best way is to show you an example. Here's an example from my system 

1) Let's rsync my Download folder to a folder called backup
2) contents of Download ```
ls Download
``` > justin@viking:~$ ls Download/
drink.m4a  opera_10.10.4742.gcc4.qt3_amd64.deb

3) let's create a backup directory. ```
mkdir backup
``` 
4) let's rsync with method A. ```
rsync -avz Download/ backup/
``` 
5) see the contents of backup/ ```
ls backup/
``` > drink.m4a  opera_10.10.4742.gcc4.qt3_amd64.deb
 See how the files were added directly in backup. 
6) Let's try method B. I've removed the files from backup, and I'm going to run rsync again ```
rsync -avz Download backup/
``` Notice the lack of a / on Download. Let's look at the contents of backup > justin@viking:~$ ls backup/
Download
 See it created a folder in backup called Download, which has the two files in it. 

The -avz flag is important as well. A: makes rsync run recursively, so it will copy files in folders. V: makes rsync verbose, so it tells you every file it copies. This option can be omitted. Z: compresses the data as it tranfers. I think this is unnecessary during non-network transfers, but it doesn't seem to help. 

Rsync is the best method for backups. It's an extremely powerful tool. check out the manual with ```
man rsync
```

---

### Post by xieu90 on 2009-11-29
thanks everyone
I use fsarchiver now.
it is like partimage ^^

---

