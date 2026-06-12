---
title: "Need to recover delete user home directory"
date: 2011-03-07
forum: General Help
---

### Post by Balask on 2011-03-07
Hello I run a server where multiple people can access it via SSH and have access to the same folder.  Someone recently decided to stop using my server so I deleted their login account inside the User and Group GUI inside gnome.  I accidentally selected delete files owned by this user.  I didn't think much of it because the user didn't actually own any of the files since it was shared among all of them.  Anyway, ALL the files in that shared home directory vanished, including the home directory.  How can I recover this?  It didn't move all the files to the root trash or my local user's trash folder.  Are the permanently deleted?

---

### Post by Kirboosy on 2011-03-07
Hi Balask! Welcome to the Forums!

You could try using the program Foremost.

[https://help.**ubuntu**.com/community/DataRecovery"]Ubuntu Data Recovery]("http://[/SIZE)
[SIZE=2]
[/SIZE]> 
**[B]Foremost**[/B]

 **Foremost**  is a command-line tool which can recover files from a number of  filesystems, including fat, ext3 and NTFS. It can be installed and run  from the live cd. 
Boot from the live cd and then enable the universe repository and install **foremost**: 
Use [any method]("https://help.ubuntu.com/community/InstallingSoftware") to install the following package: 

**foremost****Foremost**  can recover files from an image of the drive, or from the drive  directly.  If the drive has suffered hardware problems, use gnuddrescue  to image the drive first.   
Assuming  the lost files are on hda, you need to create a writeable directory on  another drive where you can put the recovered files (lets say you have a  big external usb drive (sdb) 

sudo mount /dev/sdb1 /recovery
sudo mkdir /recovery/**foremost**And then run **foremost**: 
sudo **foremost** -i /dev/hda -o /recovery/**foremost**To run formost on an image, just substitute the filename for the device 

sudo **foremost** -i image -o /recovery/**foremost**The recovered files will then be owned by root. Change their ownership so that you can use them: 
sudo chown -R youruser:youruser /recovery/**foremost**Use the -w switch to obtain only an audit of recoverable files: 

sudo **foremost** -w -i /dev/hda -o /recovery/**foremost**To recover only specific file types, use the -t switch: 

sudo **foremost** -t jpg -i /dev/hda -o /recovery/**foremost**

---

### Post by matt_symes on 2011-03-07
Hi

You could try extundelete as well.

[http://sourceforge.net/projects/extundelete/?showfeed=everything](http://sourceforge.net/projects/extundelete/?showfeed=everything)

Kind regards

---

### Post by alphaamanitin on 2011-03-07
There is also TestDisk.

AlphaA

---

### Post by Balask on 2011-03-07
> **matt_symes said:**
> Hi

You could try extundelete as well.

[http://sourceforge.net/projects/extundelete/?showfeed=everything](http://sourceforge.net/projects/extundelete/?showfeed=everything)

Kind regards


I'm having this error:

> "./configure
Configuring extundelete 0.2.0
configure: error: Can't find ext2fs library

I have both e2fsprogs and e2fslibs installed:

> balask@Balask-Server:~/Downloads/extundelete-0.2.0$ sudo apt-get install e2fsprogs
[sudo] password for balask: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
e2fsprogs is already the newest version.
The following packages were automatically installed and are no longer required:
  libaccess-bridge-java libavutil49 libx264-85 libaccess-bridge-java-jni
  ca-certificates-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
balask@Balask-Server:~/Downloads/extundelete-0.2.0$ sudo apt-get install e2fslibs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
e2fslibs is already the newest version.
The following packages were automatically installed and are no longer required:
  libaccess-bridge-java libavutil49 libx264-85 libaccess-bridge-java-jni
  ca-certificates-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.


---

### Post by oldos2er on 2011-03-07
It's probably looking for e2fslibs-dev. But, no offense to matt_symes, Testdisk might be easier: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by alphaamanitin on 2011-03-08
I like TestDisk.  Used it to recover a drive I had deleted the partitions and reformatted from NTFS to FAT32.  It is very easy to use and straight forward.


AlphaA

---

