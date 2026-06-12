---
title: "Installing wvdial"
date: 2009-07-18
forum: General Help
---

### Post by charanpreethu on 2009-07-18
Hi,
I am using Mint Gloria.I Have windows Xp also in my system.
Internet doesnot work in Mint,in order to make it work I should download wvdial.conf and edit it,but without internet how can I download it and edit it.Internet works in windows xp.Is there any way to download it in xp and edit it in mint????

---

### Post by wojox on 2009-07-18
Have you tried:

```
sudo wvdial /etc/wvdial.conf
```

Where are you downloading it from?

---

### Post by charanpreethu on 2009-07-18
If I type wvdial in terminal it asks me to download it.
If I had internet in mint I could have downloaded it using synaptic or using command line.

---

### Post by unutbu on 2009-07-18
It sounds like you need to download the entire wvdial deb package. 
Keryx is a program that runs under Windows, and allows you to download not only the deb package for Mint, but also any required dependencies. (see [http://keryxproject.org/](http://keryxproject.org/) to download Keryx, and see [http://crashsystems.net/2009/01/keryx-tutorial/](http://crashsystems.net/2009/01/keryx-tutorial/) for a tutorial on how to use it).


Here is how you can transfer the files from Windows to Linux:

Note: Windows can not read Linux partitions (ext3 filesystems) by default, but Linux can read Windows partitions (FAT or NTFS filesystems).

So use Keryx or manually download the files/packages in Windows. 
Note the place where you save the files.
Boot Linux. Click Places>Computer. You should be able to access your Windows partition from there. If you can't open a terminal (Applications>Accessories>Terminal) and type
```

sudo fdisk -l
cat /etc/fstab

```
and post the output here, and we'll setup Linux so you can access the Windows partition easily.

PS. There is also a way to setup Windows so that Windows can read and write to a ext3 (Linux) partition. (See [http://www.fs-driver.org/](http://www.fs-driver.org/))

---

### Post by Elfy on 2009-07-18
Please do not post duplicates.

[http://ubuntuforums.org/showthread.php?p=7635747](http://ubuntuforums.org/showthread.php?p=7635747)

---

