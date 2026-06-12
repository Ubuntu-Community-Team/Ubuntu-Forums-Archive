---
title: "How do I get Xubuntu to see a Win7 HDD?"
date: 2010-01-14
forum: General Help
---

### Post by s1mp13m4n on 2010-01-14
Hello everyone.  I have Xubuntu 9.10 64bit and Win7 on the same HDD in a duel boot setup.  How do I get Xubuntu to see and use the Win7 partition of the drive?  I have some video files that I want to watch from my Win7 partition.  Also, have they fixed the login screen issues with Ubuntu 9.10 yet?  Mine will never log in and this time I simply got lucky and it worked.  Thanks for the help.

---

### Post by rbc on 2010-01-15
Open synaptic and verify that you have ntfsprogs installed. That may get you started

---

### Post by Techsnap on 2010-01-15
Find your Windows drive:

```
sudo fdisk -l
```

Once you've found it:

```
mkdir /media/Windows && sudo mount -t ntfs /dev/sdx /media/Windows
```

Replace sdx with your Windows drive and you'll then be able to access it using Thunar, the final manager.

---

### Post by Leppie on 2010-01-15
add yourself to the fuse group (this will allow you to mount filesystems with your normal user account) and install ntfs-config in order to setup ntfs mounting in an easy way:
```
sudo adduser <yourusername> fuse
sudo apt-get install ntfs-config
```
if you want to change settings in ntfs-config, you will find the app under Applications>System>NTFS Configuration Tool

---

### Post by s1mp13m4n on 2010-03-15
I have ntfsprogs installed.  I ran this code in the terminal sudo fdisk -l and it only shows my linux drives.  I am trying to gain access to my 2TB external drive which is connected to a Win7 machine and is networked.  How do I get Xubuntu 9.10 to see it?  I tried what was listed above but I get error messages.  :)

---

