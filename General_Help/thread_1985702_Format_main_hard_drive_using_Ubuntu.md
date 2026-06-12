---
title: "Format main hard drive using Ubuntu?"
date: 2012-05-23
forum: General Help
---

### Post by acid1103 on 2012-05-23
I need to format my main hard drive (the one I'm on now.) there is no way to do it from my boot manager, and I don't know how to do it, if it's even possible, using Ubuntu.. Please help..
:confused:

---

### Post by iclestu on 2012-05-23
why? what is it that you are trying to achieve?

---

### Post by acid1103 on 2012-05-23
Not that it matters, but I'm trying to reinstall windows. Ubuntu is not user-friendly enough for my likings, but the disk that I have I got from this website: [http://www.renjusblog.com/2009/09/free-windows7-full-version-download.html](http://www.renjusblog.com/2009/09/free-windows7-full-version-download.html) I'm not sure if it is a repair disk or what, but it will not let me format my hard drive from the installation section... So I have to find some other way to get my hard drive to be NTFS... And that's why I'm here. :P

---

### Post by tumutanzi.com on 2012-05-23
Anyway, you should back up all your personal files and data, just in case you make mistakes.

---

### Post by tumutanzi.com on 2012-05-23
I once lost all my personal files when I re-install the OS.
Just copy all your data into another hard disk.

---

### Post by acid1103 on 2012-05-23
All of my data has already been backup-ed.. Now I just need to know how to format my main hard drive... >.<

---

### Post by jmore9 on 2012-05-23
I always use gparted live cd.  Just download it , and burn to cd.  boot from it And Pay attention to what you want to fomat

---

### Post by oldfred on 2012-05-23
You can use gparted from the Ubuntu liveCD or download a gparted liveCD. Just delete all the partitions and Windows should install.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by acid1103 on 2012-05-23
Wait... How do I delete the partions if the partions I'm trying to delete are on the hard drive that I'm using?

---

### Post by jmore9 on 2012-05-23
Its called gparted live .  That means it runs in memory / and cd.  The user can do what ever they need to do with the partitons using the live which does not use the machines hard drive.

---

### Post by choppyfireballs on 2012-05-23
What I would do is either go torrent a windows cd corresponding to your cd key use that to install (it will let you format) then acctivate it using your activation key on your computer (sticker somewhere on either the tower (if desktop) or the shell (if laptop))

if you are uncomfortable with this option because it's a torrent, download ubuntu live cd boot to it. 

open up terminal 

```
sudo apt-get install gparted 
```

and use that utility to delete drives and create unallocated space then use your windows installer to finish formatting (it will do it automatically)

The reason you could not format from a windows recovery cd is that windows does not recognize the linux format of ext1,2,3 or 4 so if you delete partitions using gparted and they are sitting as one big unallocated space pool of empty data windows will then recognize it.

ALL OF THIS CONSIDERED I would not completely remove ubuntu from your computer you should always have a second os on your computer in case you need to recover data from an infected or corrupted Windows partition.

---

### Post by kanikilu on 2012-05-23
You can't go wrong with an Ultimate Boot CD (or USB stick) around: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

