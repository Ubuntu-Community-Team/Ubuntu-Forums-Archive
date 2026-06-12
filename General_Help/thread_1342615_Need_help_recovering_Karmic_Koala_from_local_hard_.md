---
title: "Need help recovering Karmic Koala from local hard drive"
date: 2009-11-30
forum: General Help
---

### Post by powderskier9 on 2009-11-30
Good Day/Evening,

I am currently running into an issue with not being able to login to my Karmic Koala installation. 

Currently, when I login using my local hard disk, I see the following error;

"configuration defaults for gnome power manager has not been installed correctly"

Looked through the forums, a couple of people pointed out that this may be caused by a lack of drive space due to Simple Backup saving data to a folder in /home if the previously specified external hard drive was not present.

So, I popped in the Live CD, rebooted, got into the system, lo and behold, my local disk has 0 bytes of free space. I see the folder's in my /home/username/backup folder, the issue is that I cannot delete any of the items in here due to issues with permissions.

How can I mount my local disk drive from a terminal window using the original credentials while logged in with the LiveCD, so that I can free up some disk space to be able to boot into my system again? Some people mentioned a Knoppix boot CD for the permission issue.

This is a pretty bad time for my system to crash given that I am studying for an exam, any help would be greatly appreciated.

Thanks in advance, 

Mark

---

### Post by jbrown96 on 2009-11-30
1) boot the Ubuntu or Knoppix liveCD. 
2) Open a terminal (In Ubuntu Apps-->Accessories-->Terminal)
3) Create a mount point ```
sudo mkdir /media/home
```
4) Get a list of your partitions ```
sudo fdisk -l
``` This will give you a list of all your partitions. If you don't know which one is your /home partition, then you will have to try them all. 
5) Try to mount the first partition ```
sudo mount /dev/sda1 /media/home
``` Replace /dev/sda1 with the first entry from #4. 
6) Check to see if it's the right partition ```
ls /media/home
``` This should give you a list of folders. Your user folder should be there. 
7) If it's not, then unmount the partition ```
sudo umount /media/home
``` and do #5 with the next partition from #4. 

Once you get your home partition mounted, then your can go about deleting files. 
Here's the preferred method. It's harder, so you may want to skip to the easy method below.
```
sudo rm -rf /media/home/TO/DELETE
``` this will delete a folder and all its contents
```
sudo rm /media/home/*
``` that will delete the contents of the folder but not the folder
```
sudo rm /media/home/FILE
``` that will delete a file

When you start typing a directory path (i.e. /medi) press tab and it will autocomplete as much as possible. If there are multiple options then press tab again and it will list all the possibilities. This makes it much easier to type long file paths.

Easy method. 
```
sudo nautilus /media/home
``` This will open up the file browser where you can delete files graphically. Make sure to delete them, and not to send them to trash.

---

### Post by powderskier9 on 2009-12-01
[jbrown96]("http://ubuntuforums.org/member.php?u=304717");

You my friend, are a life saver. Freed up 80GB of free space from the aforementioned folder. I will be rebooting to see if I can get back into my system and will post another update in 5 minutes after a restart.

This is why open source is awesome, its not only the product, but the community that work together to help each other out. I hope that I can contribute one day to help other's out in the same way.

Thanks again for your time and assistance,

Mark

---

### Post by powderskier9 on 2009-12-01
After a restart, once the steps above had been performed as per the instructions from [jbrown96]("http://ubuntuforums.org/member.php?u=304717"), I was able to boot back into my system without seeing the previous issue. This(free up drive space) seemed to resolve the gnome error message. Another posting had indicated that this could also be caused by the gnome package needing to be reinstalled as per the following article;

[http://ubuntuforums.org/showthread.php?t=1116636](http://ubuntuforums.org/showthread.php?t=1116636)


If using Simple Backup to backup to an external drive, a useful suggestion from others was to go to System menu->Administration->Simple Backup Config->click on the Destination tab->make sure that the checkbox labelled; 

"Abort backup if destination directory does not exist" is checked. 

Otherwise, it seems that the software will write your backup's to a local backup directory versus going to an external drive.

Thanks again jbrown96, here is wishing you some good karma.

---

### Post by JBAlaska on 2009-12-01
Glad you got it running, one thing though. It's a very bad idea to run GUI programs using the sudo command, it may in some instances fubar your ".ICEauthority"

Always use gksudo as in ```
gksudo nautilus
```

---

### Post by jbrown96 on 2009-12-01
good point about gksu JBAlaska. 

There is a disk usage analyzer in Apps-->Accessories that gives you a very nice pie-chart to see where your disk space is going to help prevent this in the future.

---

