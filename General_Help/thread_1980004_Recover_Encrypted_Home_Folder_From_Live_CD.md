---
title: "Recover Encrypted Home Folder From Live CD"
date: 2012-05-13
forum: General Help
---

### Post by Bidski on 2012-05-13
This may be a stupid question. But what do you do if your Live CD does not have eCryptfs installed on it?

I also assume that by booting from the Live CD we are booting into Ubuntu and using the "Try Ubuntu" option?

Bidski

---

### Post by oldos2er on 2012-05-14
Post moved to its own thread.

---

### Post by sudodus on 2012-05-14
Hi and welcome to the Ubuntu Forums :-)

A live *ubuntu CD is not encrypted at all, but contains information to create eCryptfs. You are logged in directly at boot. If you want encrypted folders, I suggest that you install your system to an internal hard disk drive, or if you want a portable system, to a USB drive (hard disk or flash) and use no proprietary drivers.

If you want to install your system to a USB drive, I strongly recommend, that you disconnect your internal drive(s) to avoid confusion during the install procedure. During the installation, you will get an option to select encrypted folders. This also implies that the swap partition will be converted to encrypted swap.

It is also possible to make a persistent live system with a casper-rw file or partition. And here it is possible to select some encryption, but I think it is more complicated. Also it is more sensitive to data corruption (that some casper-rw data will be impossible to read and your encrypted data will be lost).

---

### Post by roelforg on 2012-05-14
> **sudodus said:**
> Hi and welcome to the Ubuntu Forums :-)

A live CD is not encrypted at all. You are logged in directly at boot. If you want encrypted folders, I suggest that you install your system to an internal hard disk drive, or if you want a portable system, to a USB drive (hard disk or flash) and use no proprietary drivers.

If you want to install your system to a USB drive, I strongly recommend, that you disconnect your internal drive(s) to avoid confusion during the install procedure. During the installation, you will get an option to select encrypted folders. This also implies that the swap partition will be converted to encrypted swap.

It is also possible to make a persistent live system with a casper-rw file or partition. And here it is possible to select some encryption, but I think it is more complicated. Also it is more sensitive to data corruption (that some casper-rw data will be impossible to read and your encrypted data will be lost).

I think he meant to recover files from his encrypted homedir (the one on the hd) with the livecd after some horrible crash or something that forces him to reinstall.

Also:
Running this in a terminal on the livecd should install the tools to mount your homedir.
```

sudo apt-get install ecryptfs-utils

```

---

### Post by mc4man on 2012-05-14
ecryptfs-utils is on the 10.04, 11.04, 11.10, 12.04 & 12.10 live cd's, so i strongly encourage using one of those than trying to boot to another image & installing the package (non-supported

I have a basic how-to here for recovery 
[http://askubuntu.com/questions/38336/how-do-i-recover-my-data-from-an-encrypted-home-directory/80386#80386](http://askubuntu.com/questions/38336/how-do-i-recover-my-data-from-an-encrypted-home-directory/80386#80386)

---

### Post by sudodus on 2012-05-14
> **roelforg said:**
> I think he meant to recover files from his encrypted homedir ...

You are probably right. Then I'd suggest this link
[[COLOR="Red"]_http://bodhizazen.net/Tutorials/Ecryptfs_[/COLOR]]("http://bodhizazen.net/Tutorials/Ecryptfs")

---

