---
title: "Strange Mount Directory Problems"
date: 2010-08-31
forum: General Help
---

### Post by Serpher on 2010-08-31
Hey. I run Fedora 13 on my home PC, and I do a fair bit of playing around with it like turning it into a LAMP server etc etc. I noticed in my Places panel that I had a random 5.4GB filesystem. I don't have any USB or external storage devices connected to my computer. I went to /media/ to see what was up and My data partition called "Data Storage" formatted as NTFS as it's where I put all my games (I have another 37GB partition with Windows 7). The directory listing goes like this along with some actions I've tried after that:

```
matt:~ %> su -                                                          {17:30}
Password: 
[root@fmain ~]# cd /media/
[root@fmain media]# ls
Data Storage  Data Storage_
[root@fmain media]# ls Data Storage_
ls: cannot access Data: No such file or directory
ls: cannot access Storage_: No such file or directory
[root@fmain media]# umount Data\ Storage_
[root@fmain media]# ls 
Data Storage  Data Storage_
[root@fmain media]# ls Data Storage
ls: cannot access Data: No such file or directory
ls: cannot access Storage: No such file or directory
[root@fmain media]# ls
Data Storage  Data Storage_  Data Storage__
[root@fmain media]# 
```

The final 'ls' came after mounting the partition again through the GUI tool. I know this isn't a big problem but I like to know why things happen, and if perhaps something isn't working quite right in my system. Is it just the imperfections of the NTFS driver for Fedora? I know Fedora is more cutting edge and is likely to run into bugs, but I'm wondering if anybody else has had this problem.

Thanks.

EDIT: Under further investigation the partition mounts into the directory with the most underscores. Is this a problem with 'umount'?

EDIT2: Oops. I noticed a noob mistake in my syntax. Let me fix that but it's still presenting a problem. I'll also try messing around with a umount alias that also includes deleting the directory it was just mounted in.




```
matt:~ %> su -                                                          {17:46}
Password: 
[root@fmain ~]# cd /media/
[root@fmain media]# ls
Data Storage  Data Storage_  Data Storage__
[root@fmain media]# ls Data\ Storage/
[root@fmain media]# ls Data\ Storage_/
[root@fmain media]# ls Data\ Storage__/
Adobe        Music              $RECYCLE.BIN               vcredist.bmp
Apps         Operating Systems  System Images              Websites
Game Images  pagefile.sys       System Volume Information
Logos        Pictures           Torrents
Movies       Programs           UB
[root@fmain media]# 
```

```
[root@fmain media]# rmdir Data\ Storage/
[root@fmain media]# rmdir Data\ Storage_/
rmdir: failed to remove `Data Storage_/': Device or resource busy
[root@fmain media]# rmdir Data\ Storage__/
rmdir: failed to remove `Data Storage__/': Device or resource busy
[root@fmain media]# ls Data\ Storage_/
[root@fmain media]# umount Data\ Storage_/
umount: Data Storage_/: not mounted
[root@fmain media]# 
```

---

### Post by shamun on 2010-09-01
i have the exactly same problem with a USB Hard Disk today.

lsof | grep /media/DIR is not returning anything

does anyone know which process is blocking the Folder?

EDIT: i use Ubuntu ;) 

i solved the problem by stopping gdm, deleting the file and restarting gdm -.-

but still the folders are not deleted properly by gnome after unmounting them

```

sudo service gdm stop
sudo rmdir /media/[DIR]
sudo service gdm start

```

---

