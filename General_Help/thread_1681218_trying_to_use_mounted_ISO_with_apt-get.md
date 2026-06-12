---
title: "trying to use mounted ISO with apt-get"
date: 2011-02-03
forum: General Help
---

### Post by gnychis on 2011-02-03
Hi all,

I do not have an internet connection or a cdrom, so I am trying to use a mounted ISO for apt-get commands.

I have this in my fstab:
```

/.iso/ubuntu.iso     /mnt/iso     iso9660 ro,loop,auto      0      0

```

And it is properly mounted:
```

gnychis@double-quad:/.iso$ ls -ltrh /mnt/iso
total 1.5M
-r--r--r-- 1 root root 1.4M 2010-07-08 12:55 wubi.exe
-r--r--r-- 1 root root  143 2010-08-16 06:17 autorun.inf
lr-xr-xr-x 1 root root    1 2010-08-16 06:18 ubuntu -> .
-r--r--r-- 1 root root  227 2010-08-16 06:18 README.diskdefines
dr-xr-xr-x 2 root root 2.0K 2010-08-16 06:18 preseed
dr-xr-xr-x 4 root root 2.0K 2010-08-16 06:18 pool
dr-xr-xr-x 2 root root 2.0K 2010-08-16 06:18 pics
dr-xr-xr-x 3 root root 2.0K 2010-08-16 06:18 dists
dr-xr-xr-x 2 root root  16K 2010-08-16 06:19 isolinux
dr-xr-xr-x 2 root root 2.0K 2010-08-16 06:19 install
dr-xr-xr-x 2 root root 2.0K 2010-08-16 06:19 casper
-r--r--r-- 1 root root 4.5K 2010-08-16 06:19 md5sum.txt

```

I made this my /etc/apt/sources.list (commenting everything else out):
```

deb file:/mnt/iso/ lucid main restricted

```

I then do sudo apt-get update:
```


gnychis@double-quad:/.iso$ sudo apt-get update
Ign file:/mnt/iso/ lucid/main Translation-en_US
Ign file:/mnt/iso/ lucid/restricted Translation-en_US
Get:1 file: lucid Release.gpg [189B]
Get:2 file: lucid Release [1,759B]
Ign file: lucid/main Packages
Ign file: lucid/restricted Packages
Ign file: lucid/main Packages
Ign file: lucid/restricted Packages
Reading package lists... Done

```

And finally get this error trying to use apt-get:
```

gnychis@double-quad:/.iso$ sudo apt-get build-dep hostapd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: You must put some 'source' URIs in your sources.list

```

Any thoughts?

Thanks!
George

---

### Post by NFblaze on 2011-02-03
Have you tried adding the CD-ROM to your sources list.

Like for my 10.04 installation. 

```
cat /etc/apt/sources.list
```

I have 
[PHP]
deb cdrom:[Ubuntu 10.04 LTS _lucid Lynz_ - Release i386 (20100429)]/ lucid main restricted
[/PHP]

Then 

```
sudo apt-get update 
```

and try again.

---

### Post by ajgreeny on 2011-02-03
Is it a live CD that you are trying to use?  If it is, I'm afraid you will not succeed; you need the alternate install CD to do that.

---

