---
title: "Ubuntu message about finding deleted files."
date: 2010-10-23
forum: General Help
---

### Post by Pavlidis on 2010-10-23
Hello, i am a newbie to the world of Linux. I recently installed to my  Acer 5920G laptop, Ubuntu 10.04, alongside with Windows 7. In order to  install Ubuntu i divided my hard disc into 4 partitions: 1. sda1  contains Windows 7 (ntfs), 2. sda2 contains data, 3. sda3 contains  Ubuntu (ext4), 4. contains swap.

Today i started my PC, and 3 error messages appeared. Now, every time i start over my PC the messages continue to appear.

The messages are:

1) Could not find "/home/pavlidis/Desktop/Ubuntistas". 
    Please check the spelling and try again.

2) Could not find "/home/pavlidis/Desktop/untitled folder".
    Please check the spelling and try again.

3) Could not find "/media/Pavlidis_".
    Please check the spelling and try again.

The first 2 messages refer to 2 folders that i had in my desktop, which i deleted. If i create 2 new folders with the names Ubuntistas and untitled folder, the 2 messages don't appear anymore. The problem is when i delete them again, the error messages, reappear.

The 3rd message i believe refers to my sda2 partition, which is named Media. I am not sure though, because the error refers  to media and not Media.

I googled the errors but everything i found referred to missing packages or applications, so a sudo apt-get or sudo update command solved them.

Can anybody tell me how to make these messages disappear, and why did they appeared in the first place?

---

### Post by Pavlidis on 2010-11-16
No one can help me with this problem?

---

### Post by drs305 on 2010-11-16
Can you still boot into Ubuntu?

If so, open fstab as root and see if you have listings for these folders. It's possible these folders are listed in fstab and the system is trying to mount them at boot.
```
gksu gedit /etc/fstab
```

If you can't boot into Ubuntu normally, use a LiveCD. From the Desktop, open a terminal (Applications, Accessories, Terminal), mount your Ubuntu partition and then check fstab:  

```
sudo mount /dev/sd**XY** /mnt
gksu gedit /mnt/etc/fstab
```
Change XY to your Ubuntu partition (example: sda1, sda5, etc)

---

### Post by harun3d on 2012-04-23
[FONT=monospace]1)Writing:[/FONT]
```
 gksu gedit /etc/fstab
```
gave
[PHP]
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=....... /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=......    none            swap    sw              0       0
[/PHP]so my missing file "/media/4GBVK/rz" is not present here.


2)Conduit (ubuntu synchronization program) synchronizes my usb  stick with my documents. and when the usb stick is missing he shows this  message.  But Conduit does not start at startup also not in the  background.  

3)      Code:
     sudo apt-get install gvfs-backends 
 did not fix it

4) Probably I have to reinstall gvfs-backends, nautilus, ubuntu-desktop and some other stuff as it is written here:  [http://ubuntuforums.org/showthread.php?t=1278395](http://ubuntuforums.org/showthread.php?t=1278395)
But it is not written how.

5)"libgnomevfs2-extra" is probably not the solution as written in another page on this forum

6) installing smbfs would probably not fix it.

7) The missing file is not any more in my favorite files list in the sidebar of the file explorer

---

