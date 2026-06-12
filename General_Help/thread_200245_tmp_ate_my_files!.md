---
title: "/tmp ate my files!"
date: 2006-06-20
forum: General Help
---

### Post by pdub on 2006-06-20
Hello,

As a new user to Ubuntu, (previously a SuSE user), and decided to use my new Ubuntu system to store some files from my parents computer while I rebuild their virus riden Windows installation. 

I proceded to create a share to the /tmp folder and named it 'temp'. I then booted their system with the Ubuntu 6.06 'live' DVD, mounted their fat32 volume and copied the data over the network (mostly pictures) to the 'temp' share on my PC. 

I then rebuilt their system and in the mean time powered off my Ubuntu PC for the night. Today when I booted my Ubuntu PC, all the files and folders that I backed up are gone from the /tmp folder. I assume this is a default behaviour for Ubuntu to clear the /tmp folder after a reboot and was probably not too smart on my part. 

My questions is, can I recover these files? 

The partition is formated with ReiserFS. Any advise would be greatly appreciated.

-PDub

---

### Post by ltmon on 2006-06-20
I've never noticed that behavious before, but I'm not really in the habit of storing anything in /tmp.

I know KDE caches a lot of stuff there, and that never seems to be deleted automatically.

As for recovery: [http://www.antrix.net/journal/techtalk/reiserfs_data_recovery_howto.comments](http://www.antrix.net/journal/techtalk/reiserfs_data_recovery_howto.comments) is the best information I found.

L.

---

### Post by nanotube on 2006-06-20
well, /tmp is cleaned out on boot. it's not called /tmp for nothing.... though i suppose it is not immediately apparent.

the link to recovering stuff from reiserfs is good if you have reiserfs. if you have ext3, however, your chances are not that good. see here: [http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html](http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html)
the question about recovering deleted files...
so things are not looking so good for you. but maybe someone with more expertise on this matter can give you something useful to try.
main thing is to not do anything with the disk in question until you make you attempt to image the disk and grep for the files, to minimize chances of the deleted files getting overwritten.

---

### Post by [S|G] on 2006-06-20
I never tried to do anything like that myself, but I have found this program: 
[http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

Sounds promising, but from reading I assume it will be utterly complicated to use. Still, you might give it a try.

---

### Post by bforbes on 2006-06-20
My suggestion is to power the computer off immediately, and boot up off a live CD. The longer you use the hard drive, the more likely the stuff will be overwritten. I've successfully recovered deleted files on an NTFS partition, but I was very careful.

---

### Post by pdub on 2006-06-20
Thanks Everyone,

I followed the instruction in the link proviced by ltmon and was able to recover all of the missing files. I am glad that I selected ReiserFS during install!

The process was:

- Boot with Knoppix
- ensure that /dev/hda2 was not mounted
- run: reiserfsck --rebuild-tree -S -l /root/recovery.log /dev/hda2
  This took about 2 hours
- copied files back to Windows computer over the network

Thanks again to all that replied. Ubuntu does indeed have a strong community!

-PDub

---

### Post by nanotube on 2006-06-20
[QUOTE=pdub]Thanks Everyone,

I followed the instruction in the link proviced by ltmon and was able to recover all of the missing files. I am glad that I selected ReiserFS during install!

The process was:

- Boot with Knoppix
- ensure that /dev/hda2 was not mounted
- run: reiserfsck --rebuild-tree -S -l /root/recovery.log /dev/hda2
  This took about 2 hours
- copied files back to Windows computer over the network

Thanks again to all that replied. Ubuntu does indeed have a strong community!

-PDub[/QUOTE]
haha that's great! i went with the default ext3, as do most people, but i am starting to think i should have gone with reiser. ;)

---

### Post by mf14 on 2006-09-08
> **pdub said:**
> 
I assume this is a default behaviour for Ubuntu to clear the /tmp folder after a reboot and was probably not too smart on my part. 
-PDub

I have figured out that the script  /etc/init.d/bootclean.sh  called by  /etc/rcS.d/S35mountall.sh  automatically cleans /tmp.  But it can be configured using  $TMPTIME  in  /etc/default/rcS  and a file called .clean in /tmp (owned by root).
This way you can adapt Ubuntu to the way you prefer.

---

