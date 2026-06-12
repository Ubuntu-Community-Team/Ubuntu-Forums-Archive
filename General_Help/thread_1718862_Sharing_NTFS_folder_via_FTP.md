---
title: "Sharing NTFS folder via FTP"
date: 2011-03-31
forum: General Help
---

### Post by hoink on 2011-03-31
I feel like there's some user/group/mount concepts I need to understand to pull this off:

I have a dual boot ubuntu/XP rig and I'm storing some active work files on an NTFS partition because so I can use these files from both OSes (because Windows can't read my ext3 partition, but ubuntu CAN read NTFS)

Now, I need to access these files (on the NTFS partition) from my 2nd computer... which means I need to config an ubuntu FTP server (currently pureftp, but I'm not picky) to serve the files on that NTFS partition.

Like I said, I'm using PureFTP, but I'm not picky.  It's not working right because of (i think) permissions and directory ownership "stuff" that I don't quite understand.  Add "mounting" the NTFS drive to the mix, and my brain fails.

I'm not too terribly afraid of a non-GUI ftp server, so if anybody can offer some guidance, concepts or general clue-sticking about how I can get the NTFS mount and permissions and the ftp user context sorted out, I'd appreciate it.

---

### Post by eltommo on 2011-04-01
Open up a terminal and type
```

sudo apt-get install ftpd

```
This will install an ftp server on your machine and it will always run on system boot.
To quickly test it, type
```

ftp localhost

```
then enter your username and password when prompted. If it said connection refused, then it didn't work. Press ctrl+d to exit.
If you used the ubuntu gui to mount the ntfs partition on your machine, then it will be under the directory 
/media/<some name or string of numbers>
and you should be able to use your ftp client program to access this directory.

---

### Post by suryaworldedu on 2011-04-01
Thanks. Nice information!

---

