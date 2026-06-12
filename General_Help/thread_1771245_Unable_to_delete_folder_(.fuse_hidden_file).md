---
title: "Unable to delete folder (.fuse_hidden* file)"
date: 2011-05-30
forum: General Help
---

### Post by flitbee on 2011-05-30
I am running the latest version of Ubuntu (Ubuntu 11.04) which i setup as a dual boot OS with Windows XP SP3. I was listening to my MP3s using the Banshee music player on Ubuntu. My MP3s reside on an NTFS drive (which I mounted in Ubuntu to hear the MP3s). Via the Banshee player I deleted all songs from a particular folder and thought nothing of it until I later booted into Windows. 

I saw the folder that had the songs I had deleted the songs and and thought I'd delete the folder as well except that I couldn't. It said the file might be corrupted. I logged backed into Ubuntu (Windows XP was shutdown not hibernated as I remember hearing that on Hibernating, you can't properly delete/copy files on Windows partitions). In Ubuntu too, I wasn't able to delete this folder - either via the Folder explorer or via terminal. I see a file named ".fuse_hidden0000041b00000017" along with some other files I had deleted (in Turquoise colour). 

I didn't see any posts in this forum with a help on resolving this issue. The only similar [one]("http://ubuntuforums.org/showthread.php?t=1513435&highlight=.fuse_hidden") I found had no solution. 

Any ideas on how to? This hidden fuse file takes up some disk space and I want to reclaim it. Anybody?

---

### Post by cmcanulty on 2011-05-30
in terminal gksudo nautilus then it will open file system in GUI and you can delete anything be careful! If hidden select view and make sure show hidden files is checked

---

### Post by flitbee on 2011-05-30
> **cmcanulty said:**
> in terminal gksudo nautilus then it will open file system in GUI and you can delete anything be careful! If hidden select view and make sure show hidden files is checked
Wow that worked! All I wanted to was delete the offending folder and it did! Thank you [cmcanulty]("http://ubuntuforums.org/member.php?u=36066")

---

### Post by informatician on 2012-03-12
Does anyone have any tips about deleting the .fuse_hidden* file from the command line? 
sudo rm doesn't work for me.

Thanks.

---

### Post by Gizim on 2012-04-05
> **informatician said:**
> Does anyone have any tips about deleting the .fuse_hidden* file from the command line? 
sudo rm doesn't work for me.

Thanks.

BUMP same thing i need this in CLI

---

### Post by cupoange on 2012-04-09
bump, same issue need CLI

---

### Post by oklokl on 2012-04-10
[http://cafe.daum.net/candan/KUkA/3](http://cafe.daum.net/candan/KUkA/3)
I enjoy how to use
Remove useless files

mkdir -p ~/downloads/backupfile
echo "" ~/downloads/del_list.txt

chmod 755 del.sh


###### del.sh ######

#!/bin/bash
find /media/1234/1234/ -name ".swp" >> ~/downloads/del_list.txt
find /media/1234/1234/ -name ".Trash-*" >> ~/downloads/del_list.txt
find /media/1234/1234/ -name "*.db" >> ~/downloads/del_list.txt
find /media/1234/1234/ -name ".*" >> ~/downloads/del_list.txt

## backup 
find /media/1234/1234/ -name ".swp" -exec cp -rf {} ~/downloads/backupfile/ \;
find /media/1234/1234/ -name ".Trash-*" -exec cp -rf {} ~/downloads/backupfile/ \;
find /media/1234/1234/ -name "*.db" -exec cp -rf {} ~/downloads/backupfile/ \;
find /media/1234/1234/ -name ".*" -exec cp -rf {} ~/downloads/backupfile/ \;

## remove
find /media/1234/1234/ -name ".swp" -exec rm -rf {} \;
find /media/1234/1234/ -name ".Trash-*" -exec rm -rf {} \;
find /media/1234/1234/ -name "*.db" -exec rm -rf {} \;
find /media/1234/1234/ -name ".*" -exec rm -rf {} \;


or

 sudo find /media/1234/1234/ -name ".*" -exec rm -rf {} \;

---

### Post by Thorsen V on 2012-04-10
[http://ubuntuforums.org/showthread.php?t=550145&highlight=fuse_hidden](http://ubuntuforums.org/showthread.php?t=550145&highlight=fuse_hidden)
This

---

### Post by prarobo on 2012-04-18
> **cmcanulty said:**
> in terminal gksudo nautilus then it will open file system in GUI and you can delete anything be careful! If hidden select view and make sure show hidden files is checked

Thanks :p:p

---

