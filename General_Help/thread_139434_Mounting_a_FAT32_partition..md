---
title: "Mounting a FAT32 partition."
date: 2006-03-04
forum: General Help
---

### Post by thomas505 on 2006-03-04
I am dual booting windows and breezy badger. And there are some files that i want to be accesible to both operating systems. To this end i have created a 1g FAT32 partition using partition magic in windows but when i go into linux i am unable to mount it getting errors like 'unsupported filesystem FAT32'. Is there a way to fix this? (i can reformat the partition to another file system if FAT32 is a problem however i'll only do this if the file system is accessible by both windows and linux)

Thanx in advance for your help.

---

### Post by ebash on 2006-03-04
Can't you show us the contents of the file /etc/fstab?  

Also perform the following command and post it's results:
sudo fdisk -l


Here is an example on how I do to mount a fat partition.
/dev/sda2       /Windows/Data    vfat    rw,uid=emmanuel,gid=admin,umask=0000,dmask=0000,fmask=0000  0 0

---

### Post by akiro.yamamoto on 2006-03-04
Ensure the entry for the partition in the /etc/fstab file is similar to:
/dev/hdd2       /media/data     vfat    user,umask=000        0       0

---

### Post by akiro.yamamoto on 2006-03-04
You can also format the partition in Ubuntu using gParted as Fat32 or Ext3.
If you use Ext3 you will need the windows ext driver to access the partition from windows. But ext3 is a much better filesystem that Fat32.

---

### Post by handy on 2006-03-04
You need to edit your **/etc/fstab** file

& then create a folder in  **/media/** with the name that you called the drive when you edited the **fstab** file.

This info' is all through this forum if you search.

It is also in the **Ubuntu Online Help** on your computer:

**Ubuntu 5.10 Starter Guide / Windows Partitions**

The online help that comes with Ubuntu is great, nothing like the rubbish that comes with windoze! :KS

---

### Post by thomas505 on 2006-03-04
Thanks for the advice. I had to reinstall ubuntu as i did a very stupid thing. Now linux recognises the partition (hda4) as fat32 and is allowing me to read the files off of it. Now my problem is that i need to change the permisions to it so that i can write to it as well. 

Any help would be appreciated.

---

### Post by handy on 2006-03-05
**umask=0000** will make your **fat32** partition readable & writeable by everyone, a copy of the line for my fat32 partition is below:

**/dev/hdc6	/media/winlin	vfat	umask=0000	0	0**

That should do it for you! :KS

---

### Post by thomas505 on 2006-03-05
thank you for your help the problem has been resolved.

---

