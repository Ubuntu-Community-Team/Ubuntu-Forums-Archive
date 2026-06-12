---
title: "add partitions to Ubuntu path?"
date: 2010-06-24
forum: General Help
---

### Post by ilmer on 2010-06-24
Hi!

I need some help with path setup in Ubuntu (I think).

I currently am using a dual-boot setup with Ubuntu 10.04 and Win7. I have each operating system on a separate partition and furthermore I have an additional partition (/dev/sda5) which I have mounted through the NTFS configuration tool as /media/Data on which I keep my data and which is accessible from both operating systems.

In my home directory I replaced the standard Documents, etc, directories with links to directories on my Data partition.

While trying to run a program I encountered a problem, which was basically the program stating a certain file didn't exist. The path to this file is actually defined in a compilation file for the program and I am certain it is referring to the correct directory where the file indeed is located. To double check I actually used to "locate" command and to my surprise the file wasn't found. Nor can locate find any other file that I have in for example my Documents directory. It only seems to find files that are actually on the same partition as my Ubuntu install.

Is there some way I can add my Data partition to the Ubuntu search path or something, so that locate can find the files? I hope that that might also resolve my original problem.

Thanks!

---

### Post by colorlessprism on 2010-06-24
I think you may need to install NTFS-Config. Ubuntu has a graphical configuration tool for enabling read/write on NTFS partitions. This should allow read/write access whether from a Windows/Linux dual boot system or from external hard disks. To install it type:

```
sudo apt-get install ntfs-config
```

To start the GUI you can reach it:

System>Administration>NTFS Configuration Tool.

NTFS-Config should auto detect your NTFS partitions and afterwards you can enable write support for them.

You may need to play around with permissions on this partition. After a fresh install my "Media" partition allows root access only. a quick "chown" solves the problem.

---

### Post by ilmer on 2010-06-24
I really apreciate your suggestion but I do have ntfs-config, that's what I meant when I said how I have the partition mounted. I generally have no problem whatsoever accessing or writing files on the partition. It is just that when I type a locate command in the terminal it doesn't find any of the files on the partition.

I tried your chown suggestion however but it doesn't seem to work, all permission remain as root.

---

### Post by weemadarthur on 2010-06-24
The locate command uses a database created by the updatedb command when searching for files. This database is configured to not search certain paths, like remotely mounted nfs folders for example. 
Look at man updatedb.conf for details, and the PRUNE_BIND_MOUNTS in particular. You might need to set this to 0 for updatedb to index the files in your data partition.

---

### Post by dcstar on 2010-06-24
> **ilmer said:**
> Hi!

I need some help with path setup in Ubuntu (I think).

I currently am using a dual-boot setup with Ubuntu 10.04 and Win7. I have each operating system on a separate partition and furthermore I have an additional partition (/dev/sda5) which I have mounted through the **NTFS** configuration tool as /media/Data on which I keep my data and which is accessible from both operating systems.
.........

NTFS does not support all the attributes Linux requires, there is no guarantee that foreign filesystems will ever by supported by Linux system tools like updatedb which are designed for Linux filesystems.

---

