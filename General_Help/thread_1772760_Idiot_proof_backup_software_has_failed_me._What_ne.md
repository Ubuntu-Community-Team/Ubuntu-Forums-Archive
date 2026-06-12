---
title: "Idiot proof backup software has failed me. What next?"
date: 2011-06-01
forum: General Help
---

### Post by unagimiyagi on 2011-06-01
Hi,

I've tried: back in time, deja-dup, simplebackup, and none of them complete successfully.  On two different macs installed with natty.

What I want to do is to copy my /  (my entire hard drive) to an external partition.

I've got a variety of errors, which range from permission errors (can't handle b/c I don't have access to read a folder), to not being able to copy a special file.  

How do you copy not only my home folder, but also preferences?  I would want my /etc/X11/xorg.conf file, as well as some of my "preferences" copied.  I don't know if I need /etc , /proc, /dev, /sys, /usr directories copied or not.  

Please help.  In mac or windows, dragging and dropping has NEVER been a problem.  I should be able to drag and drop any folder I well please.  I've also tried gksudo nautilus as well.  Please tell me what to backup.  I want this to be as easy as time machine is. 

Thanks

---

### Post by mastablasta on 2011-06-01
mintbackup is a nice tool for backing up prepferences. it has two buttons one for backing up home the other one to backup your preferences.
 
for what you want to do you need a clonezilla and possibly run it from live CD and create a clone of the disk.
 
you can't copy the files that the system is using! same is in windows. try running via live CD.
 
also i think user should NOT be given easy access to all files. as if user has easy access then viruses and malware have it too.

---

### Post by Irihapeti on 2011-06-01
If you are just wanting to backup your installation, I'd suggest something like [TAR]("https://help.ubuntu.com/community/BackupYourSystem/TAR"). I've used it and similar programs successfully over several years.

It looks a bit complicated, but once you've decided what you want to do, it can be put into a script. It will need to be run using sudo, of course.

---

### Post by glene77is on 2011-06-01
> **unagimiyagi said:**
> Hi,


What I want to do is to copy my /  (my entire hard drive) to an external partition.



Una,
Since my first disk crash in 1979, I have kept my "created data" on different media / partitions.
That makes the OS backup / reinstall simpler. 

Here is what I have done on my several Linux systems. 
(1) Have used Gparted from a running OS and sometimes have conflict with the running OS. 
(2) Have tried a simple Terminal   "cp"  approach, and found the OS will not fully  copy itself. 
(3) Have SUCCESSFULLY used Parted-Magic Live-CD to  Resize / Move / Backup an OS partiton.  
       (Backup works like a simple copy/paste routine on the "un-mounted" HD partitions). 
(4) Have come to rely on Live-CD for re-install of Linux OS.    

On Puppy Linux ,  
(1) used Parted-Magic Live-CD to copy / paste the old partition into a new partition. 
(2) Simply altered the grub/menu.lst code to point to the new partition,    and booted right in !   :)

On TinyCore Linux, 
(1) running Parted-Magic Live-CD,
(2) used the FileManager to simply  "cp"  copy the OS subdir from one place to another. 
(3) Altered the booting grub/menu.lst  and re-booted !

That sounds like what you want to do, 
and I suggest the Parted-Magic Live-CD  because 
(1) it runs totally in RAM,   
(2) with the HD  unmounted,  
(3) based on standard Gparted.  

On Ubuntu, 
always keep ALL created data on a different partition. , 
and use Grsync to back-up data to external USB drives.   
Because of my mucking and hacking,  :) 
I have wiped the Ubuntu OS partition several times and simply re-installed.   

HTH,

---

### Post by sbraz on 2011-06-01
this is more or less how i normally do it:

boot from a live cd/usb distro (i like partedmagic but any should do)

gain root access


**[COLOR="Red"]USE DD WITH CARE, IT CAN DESTROY DATA[/COLOR]**
create an image of a drive: d**d if=/dev/sda of=~/disk1.img bs=4M**
clone a drive (my favourite lol): **dd if=/dev/sda of=/dev/sdb bs=4M**

there are MANY optimizations and tweaks, for example compressing the image with gzip after writing zeros to the empty spaces of the drive.  

[http://www.cyberciti.biz/tips/how-do-i-make-linux-filesystem-backup-with-dd.html](http://www.cyberciti.biz/tips/how-do-i-make-linux-filesystem-backup-with-dd.html)
[http://www.backuphowto.info/linux-backup-hard-disk-clone-dd](http://www.backuphowto.info/linux-backup-hard-disk-clone-dd)

partedmagic is an awesome live cd, try it. :)

---

### Post by unagimiyagi on 2011-06-02
Thanks for the tips.  Can someone tell me which folders in addition to the home folder that I will need in order to save my preferences?

In other words, do I need to back up /etc? /sys? /var? /usr?

I would like a list so that I don't have to clone the drive.

---

### Post by Irihapeti on 2011-06-02
Most system-wide preferences are in /etc, and I've seen it suggested to back this up as well as the home directory. Personally, I think I've only ever restored an /etc file once or twice in nearly 4 years of using Ubuntu, so I don't think it achieves much in practice.

The others you've listed aren't needed, unless you want to save the .debs downloaded during updates, or log files. Then /var might be worth including.

---

