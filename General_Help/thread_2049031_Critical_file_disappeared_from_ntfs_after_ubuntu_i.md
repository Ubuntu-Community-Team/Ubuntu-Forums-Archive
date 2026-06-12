---
title: "Critical file disappeared from ntfs after ubuntu installation"
date: 2012-08-27
forum: General Help
---

### Post by pawelmand on 2012-08-27
I wanted to upgrade a very old version of ubuntu to recent one so I made the following steps:
1) I created a large (over 30GB) tar.gz archive containing all data from my home directory
2) Moved it to ntfs partition
3) Launched ubuntu (12.04) from cd
4) Resized the ntfs partition during installation
5) Completed the installation

Then I launched my brand new ubuntu and wanted to copy the archive so:
1) I mounted the partition on which the archive was located
2) I have run 'ls -l' in the place of filesize, modification date etc. '?' appeared instead of any values
3) I launched Windows XP which is installed on the same machine and it did not show that file on the partition at all :(
4) Linux also does not show the file anymore :(

I tried running chkdisk under windows which did not fix the problem. I also tried ntfsundelete in Linux which shows that this file cannot be recovered. 

I would appreciate any help very much! I have lost a lot of data. What could have happend? Is there any chance of recovering this file?

---

### Post by dcstar on 2012-08-28
> **pawelmand said:**
> I wanted to upgrade a very old version of ubuntu to recent one so I made the following steps:
1) I created a large (over 30GB) tar.gz archive containing all data from **my home directory**
2) Moved it to ntfs partition
............

You **cannot** put System Folders on non-Linux filesystems, NTFS is **not** a Linux filesystem.

---

### Post by Statia on 2012-08-28
> **dcstar said:**
> You **cannot** put System Folders on non-Linux filesystems, NTFS is **not** a Linux filesystem.

But he did not put system folders on NTFS, he put one file on it: a tar.gz. All folders and file attributes and metadata that NTFS would not handle are "inside" the tar.gz, so it should not matter, for NTFS it's just a file. Or am I wrong in assuming this?

---

### Post by coffeecat on 2012-08-28
> **Statia said:**
> But he did not put system folders on NTFS, he put one file on it: a tar.gz. All folders and file attributes and metadata that NTFS would not handle are "inside" the tar.gz, so it should not matter, for NTFS it's just a file. Or am I wrong in assuming this?

You are correct. In the past I've made tar.gz files of complete Linux installations, and stored the tar.gz files on NTFS filesystems. After unpacking the tar.gz file into a different ext4 or ext3 filesystem (and fiddling with UUIDs, /etc/fstab and grub) I've successfully restored a working system on the new Linux filesystem. **Many times.** As you say, all the metadata are stored in the tarball. 

I think the OP's problem may stem from this:

> 2) Moved it to ntfs partition
3) Launched ubuntu (12.04) from cd
4) Resized the ntfs partition during installation

@pawelmand, please clarify. Did you resize the NTFS partition **after** storing the tar.gz file on it? If so, for future reference, this is very unwise. Before resizing partitions, make sure that you have complete backups of all files on at least one other separate physical medium. 

But this doesn't help your immediate problem. Please expand on this:

> I also tried ntfsundelete in Linux which shows that this file cannot be recovered. 

What exact message did you see?

However, NTFS is a Microsoft filesystem and if you are trying to undelete files you would be better off with a Windows undelete application. I'm not familiar with any, so I cannot make a specific recommendation, but someone else might. Or googling may come up with something useful but, as ever, be cautious with free Windows software. If you find something that might appear to be suitable, I suggest you do some research first to be sure that it is not riddled with malware.

---

