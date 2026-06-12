---
title: "Set up an Ubuntu Windows Backup Server"
date: 2010-12-30
forum: General Help
---

### Post by Ranger1230 on 2010-12-30
I want to set up a windows backup server hosted by some linux distro (preferably with GUI) so that windows can connect to it as a network drive to store files and folders on. the server is behind a firewall so the extent of security would be a log in. if there is a tutorial on how to do this then post the link and I will worship you.

---

### Post by drdos2006 on 2010-12-30
If you need Windows to access the server then the disk or the partition to access needs to be formatted to NTFS.

Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by pricetech on 2010-12-30
> **drdos2006 said:**
> If you need Windows to access the server then the disk or the partition to access needs to be formatted to NTFS.



This is simply not true.  Windows neither knows nor cares how the drive is formatted when it's shared over a network, it just needs to be able to access it.

Easy Samba Setup:

[http://ubuntuforums.org/showthread.php?t=1644585]("http://ubuntuforums.org/showthread.php?t=1644585")

---

### Post by Ranger1230 on 2011-01-01
I think I got samba working right. but now I have a problem where I can't get any user but the account I created during the os install "rahh" to write to the disk. they have read only access. when I go to the mounted disk and look at permissions it says "The permissions of "Disk1" could not be determined. I'm guessing I need to set the permissions in order for other accounts to get write access. how do I do that for a RAID disk?

I'm using the disk utility to create the RAID disk and its a RAID 1 array.

---

### Post by pricetech on 2011-01-03
Use the Samba configuration tool System - Administration - Samba to assign whatever rights you want to your shares.

---

