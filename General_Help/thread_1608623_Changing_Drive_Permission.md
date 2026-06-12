---
title: "Changing Drive Permission"
date: 2010-10-29
forum: General Help
---

### Post by namich2007 on 2010-10-29
Hey all,

My co-worker has screwed up his Mac OSX laptop. I need to copy his file from the hard disk so we can re -install the OS over. I have hook up his disk..via a external USB drive .. to my Ubuntu 10.04 system which mounted with no problems. I can navigate to his user account and see all his desktop,document and other data storage areas, but I am unable to read or write to this disk. I want to take over the drive by changing his permissions or whatever that will let me access his files. I have done the following:

namich@nambuntu:~$ mount | grep '^/dev'
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
/dev/sdf2 on /media/Macintosh HD type hfsplus (rw,nosuid,nodev,uhelper=udisks)

So this tells me the disk in question is Device sdf2 and is mounted on  /media/Macintosh HD type hfsplus

I have also tried the following to change the permission but no success:

namich@nambuntu:~$ sudo chmod -R 755 /media/Macintosh HD
[sudo] password for namich: 
chmod: cannot access `/media/Macintosh': No such file or directory
chmod: cannot access `HD': No such file or directory

How do I overcome this issue. Any help would be appreciated

Thanks

---

### Post by malcmail on 2010-10-29
Am I right in saying there's a space in the folder name? I had that problem before and you need to "escape" it to get it to work. Easiest way is when you type out the folder name type the first part ie Mac - then press tab and hopefully it will autocomplete with the correct (odd looking) text. 

BTW if thats teaching you to suck eggs, apologies.

---

