---
title: "Dual Booting Ubuntu x32 and Fedora x64"
date: 2010-09-13
forum: General Help
---

### Post by Janitor-Blue on 2010-09-13
I currently have Ubuntu 10.04 LTS 32bit installed on a machine and I would like to attempt to set up a dual partition so I can also have Fedora 13 64bit installed at the same time. The Ubuntu installer had a pretty user friendly interface that allowed partitioning directly from the installer. Fedora doesn't appear to have such user friendly controls. Is there a way to create 2 partitions on my system without damaging my Ubuntu installation? Or will I need to start from scratch? Also, is there a way to have a shared folder between Fedora and Ubuntu? I know services like dropbox exist, but I'd prefer a local folder that does this. 
 
Any help?

---

### Post by 3Miro on 2010-09-13
You can run Ubuntu from live CD and start Gparted to edit your partitions (you can also do that form Fedora's liveCD). There is an option to "resize" partitions without deleting/formating, however, it is best to backup everything important from your system before you mess with partitions. (I am somewhat skeptical about the entire resize thing, I have seen it work, but I will not trust it with anything valuable)

---

### Post by oldfred on 2010-09-13
Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

Fedora, I think is the one that installs a boot partition & LVM for the main install, but you can create partitions and install there. It should give you a choice on where to install the boot loader. Do not install to the MBR, but if you do just reinstall grub2 from Ubuntu's partition and sudo update-grub to find Fedora.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

