---
title: "mounting ntfs-3g"
date: 2009-11-27
forum: General Help
---

### Post by Mystiques on 2009-11-27
Here is what i have done 
 
$ sudo mkdir mount 
$ sudo mount  /dev/sdb2 /media/sdb2
$ sudo ntfs-3g /dev/sdb2 /media/sdb2
 
RESULTS
 
$logfile indicates unclean shutdown (0,0)
Failed to mount '/dev/sdb2': operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:
 
Choose 1: If you have windows then disconnect the external devices by clicking on the 'safely remove hardware' icon in the windows taskbar then shutdown windows cleanly.
 
Choose 2: If you dont have windows then you can use the 'force' option fo rown responsiblity. Example
 
Mount -t  ntfs-3g -0 force /dev/sdb2 /media/sdb2
 
Or add the option to the relevant row in the /etc/fstab file:
 
/dev/sdb2 /media/sdb2 ntfs-3g force 0 0
 
 
What should i do? because i want to write on that particular volume

---

### Post by oldfred on 2009-11-27
You have to have a mount point or name like data:
sudo mkdir /media/data
sudo mount  /dev/sdb2 /media/data

See these sites:

These will provide the additional detailed steps:
HowTo Mount NTFS Partitions Read Write in Ubuntu & Kubuntu
[http://ubuntu.swerdna.org/ubuntfs.html](http://ubuntu.swerdna.org/ubuntfs.html)
Auto mount NTFS Partition
[http://ubuntuforums.org/showpost.php?p=7342606&postcount=10](http://ubuntuforums.org/showpost.php?p=7342606&postcount=10)

If you want to permanently mount it is easier to use Storage Device Manager:
But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager

---

