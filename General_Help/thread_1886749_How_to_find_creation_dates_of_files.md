---
title: "How to find creation dates of files"
date: 2011-11-25
forum: General Help
---

### Post by hanansela on 2011-11-25
Hello
My Ubuntu One synchronization have set all files to the same "last modified date". The "last accessed" information is also modified by Ubuntu One synchronization.  I need to move old files to archive folder but i can't do that since all files have the same "last modified date". I know that ext4 file system is storing creation dates but i do not know how to implement the "creation date" information in commands such as "find". Please help

---

### Post by raja.genupula on 2011-11-25
use ```
stat filename
```

---

### Post by pretty_whistle on 2011-11-25
I too wonder how to get creation date but stat filename didn't work for me.  It says no such file or directory.

---

### Post by JamesKenny on 2011-11-25
what about 

```
ls -lar /
```

or with find an xargs

```
find .| grep php$ |xargs ls -lar /
```

---

### Post by jocko on 2011-11-25
> **pretty_whistle said:**
> I too wonder how to get creation date but stat filename didn't work for me.  It says no such file or directory.
Of course you have to use the actual filename (and correct path), not "filename"...

---

### Post by raja.genupula on 2011-11-25
yeah i think so .

for example 


assassin@assassin-ubuntu:~$ stat umplayer_0.95_i386.deb 
  File: `umplayer_0.95_i386.deb'
  Size: 2093324   	Blocks: 4096       IO Block: 4096   regular file
Device: 801h/2049d	Inode: 2892905     Links: 1
Access: (0664/-rw-rw-r--)  Uid: ( 1000/assassin)   Gid: ( 1000/assassin)
Access: 2011-11-22 20:30:24.380883285 +0530
Modify: 2011-05-23 16:58:52.000000000 +0530
Change: 2011-11-20 18:24:53.802734082 +0530

---

### Post by hanansela on 2011-11-25
Thank you for your replies. however, they all give information as listed below and not the actual first creation date.  
```
File: `090520.twl'
  Size: 24201         Blocks: 48         IO Block: 4096   regular file
Device: 806h/2054d    Inode: 1442379     Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1000/   hanan)   Gid: ( 1000/   hanan)
Access: 2011-11-24 21:54:54.857139431 +0200
Modify: 2011-07-21 21:18:06.000000000 +0300
Change: 2011-11-18 07:05:34.620994467 +0200
```my problem is that all access dates start in the day i have   started Ubntu One so i cant find  which are old files.

---

### Post by pretty_whistle on 2011-11-25
> **jocko said:**
> Of course you have to use the actual filename (and correct path), not "filename"...
I put the actual filename, however I didn't put the path.

---

