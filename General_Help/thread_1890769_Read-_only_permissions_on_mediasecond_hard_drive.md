---
title: "Read- only permissions on media/second hard drive"
date: 2011-12-04
forum: General Help
---

### Post by che47audio on 2011-12-04
Hi there,

I'm a newbie so please be patient. I am running ubuntu 11.10 installed on a 160gb hard disk with no partitions. I also have a second drive, a 1tb drive which I keep all of my media e.g music & pictures on - this is the drive I have the issues with. 

There are two issues. 
The first issue is that this 1tb drive doesn't not mount automatically when ubuntu boots up, it only mounts when you access a file/s on it and with it being a sata drive this sometimes takes that annoying few seconds to respond. How can I get this to be mounted when ubuntu first boots?

And secondly, there seems to be a permissions problem with the drive. I only seem to have read-only permissions at the moment and when trying to change the permissions of the folders on the drive I just have greyed out dropdown menus which I can't change. The mount point of this drive/the folder also has a padlock symbol over it.

Any help would be greatly appreciated.

che47audio

---

### Post by che47audio on 2011-12-04
Anyone?

---

### Post by BC59 on 2011-12-04
The second drive has NTFS file format?

---

### Post by BC59 on 2011-12-04
To mount the drive automatically follow the instructions [here]("https://help.ubuntu.com/community/AutomaticallyMountPartitions"):

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

If you have any trouble to do it post your questions.

---

### Post by BC59 on 2011-12-04
If your second drive is NTFS then install this package:

```
sudo apt-get install ntfs-3g
```


> NTFS-3G uses FUSE (Filesystem in Userspace) to provide support for the NTFS
filesystem used by Microsoft Windows. It can:

 * create, remove, rename, or move files, directories, hard links, and streams;
 * read and write files, including streams, sparse files, and transparently
   compressed files;
 * handle special files like symbolic links, devices, and FIFOs;
 * provide standard management of file ownership and permissions, including
   POSIX ACLs.

This package also contains the tools previously available in the ntfsprogs
package.

---

### Post by LadySapphira on 2011-12-04
BC59 is right... and just to clarify in case you don't know NTFS format is really common, esp associated with windows.  So if your extra harddrive is formatted that way you'd be able to read but not write to it.  What BC59 mentioned works, at least it has for me.

---

### Post by che47audio on 2011-12-05
Thanks for the responses. The second drive is fat32. If I open the properties of the folder where the drive is mounted (/home/chris/media)it says the owner is root and I do not have the privileges to change this.
I have tried the "chown" command in the terminal on this folder in attempt to change the read, write, execute permissions and I get an error returned "operation not permitted". So I don't seem to be able to change the permissions even as root?!?

---

