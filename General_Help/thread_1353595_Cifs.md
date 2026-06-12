---
title: "Cifs"
date: 2009-12-12
forum: General Help
---

### Post by simonbonner on 2009-12-12
I recently upgraded from Intrepid Ibex to Karmic Koala, and I'm having problems with copying backups to my IOMEGA Home Network Drive. I mount the drive using mount.cifs and use rsync to copy backups from my laptop to the drive, updating the new files and deleting the old backups. 

This all worked in Ibex, but it's giving me a real headache in Koala. I'm using SBackup, and each backup includes several files but the main one it the single archive files.tgz. In my current backup this file is just over 5.3 GB. When I run rsync it says that it has copied that much data, but when I list the contents of the drive with ls it tells me that the size of the file on the drive is only 1.2 GB. It also says that the total size of the directory is 5.3 GB -- but that not what I get when I sum the sizes of the individual files and there aren't any hidden files in the directory. 

Has anyone seen this behaviour before? What does it mean that the total size of the directory is 5.3 GB, but the sum of the individual file sizes is well below? This is driving me nuts!


The entry in /etc/fstab is: 

//192.168.0.110/Simon		/media/simon_share  cifs users,guest,noserverino,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

Here's a transcript of my session (copy_simons_backups.sh) is just a wrapper around rsync.

519[19:54:23] ~>  sudo bin/copy_simons_backups.sh
Syncing backups...
building file list ... done
./
2009-12-12_16.32.07.897901.Piglet.ful/
2009-12-12_16.32.07.897901.Piglet.ful/excludes
2009-12-12_16.32.07.897901.Piglet.ful/files.tgz
2009-12-12_16.32.07.897901.Piglet.ful/flist
2009-12-12_16.32.07.897901.Piglet.ful/fprops
2009-12-12_16.32.07.897901.Piglet.ful/packages
2009-12-12_16.32.07.897901.Piglet.ful/partitions
2009-12-12_16.32.07.897901.Piglet.ful/ver

sent 5625852023 bytes  received 151 bytes  4231554.85 bytes/sec
total size is 5625164862  speedup is 1.00
Unmounting /media/simon_share...

520[20:16:37] ~>  sudo mount /media/simon_share 
[sudo] password for sbonner: 

521[20:27:06] ~>  ls -l /media/simon_share/Backup/
total 0
drwxrwxrwx 1 root root 0 2009-12-30 20:20 2009-12-12_16.32.07.897901.Piglet.ful

525[20:36:41] ~>  ls -lah /media/simon_share/Backup/2009-12-12_16.32.07.897901.Piglet.ful/
total 5.3G
drwxrwxrwx 1 root root    0 2009-12-30 20:30 .
drwxrwxrwx 1 root root    0 2009-12-09 07:11 ..
-rwxrwxrwx 1 root root  251 1921-08-01 09:11 excludes
-rwxrwxrwx 1 root root 1.3G 2009-12-12 20:54 files.tgz
-rwxrwxrwx 1 root root  11M 1921-08-01 09:11 flist
-rwxrwxrwx 1 root root 3.9M 1921-08-01 09:11 fprops
-rwxrwxrwx 1 root root  41K 1921-08-01 09:11 packages
-rwxrwxrwx 1 root root  259 1921-08-01 09:11 partitions
-rwxrwxrwx 1 root root    4 1921-08-01 09:11 ver

Thanks!!

---

