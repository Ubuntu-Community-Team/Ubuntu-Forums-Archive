---
title: "Is there no way to backup Unbuntu?"
date: 2011-10-09
forum: General Help
---

### Post by cybernetic toaster pastry on 2011-10-09
I posted this here because there is no backup & restore section

I have been at this for months now and this is what I have:

When I try Remastersys I try to boot the custom.iso and it leaves me with a blank black screen right after the bois. Nothing happens

When I try 
```
tar -cvpzf backup.tar.gz --exclude=/backup.tar.gz --exclude=/proc 
--exclude=/lost+found --exclude=/sys --exclude=/mnt 
--exclude=/media --exclude=/dev / 
```I get dropped into the busybox. Because it can't find the kernel or something

And I can't even get relinux to work at all

Please help

---

### Post by mike555 on 2011-10-09
in remastersys dvd you might need to boot in safe graphics mode , relinux is terminal based and you need to type "  sudo relinux iso " without quotes......... when it's done burn the .iso to dvd as image .. (worked for me)

---

### Post by vajorie on 2011-10-10
In case you give up on trying to create an iso image of your installation, here's what I do to backup: 

1. buy external hard drive
2. format it to ext3
3. mount it, note where it got mounted
4. 

```

sudo rsync -av --delete --progress --exclude '.gvfs' /home/username /media/EXTERNALDRIVE-MOUNT-POINT/    # be careful about where there are a "/"
sudo rsync -av --delete --progress /etc /media/EXTERNALDRIVE-MOUNT-POINT/    # this is just so I can reference back if I need to recover
dpkg --get-selections > /media/EXTERNALDRIVE-MOUNT-POINT/list-of-installed-packages.txt

```

5. unmount drive till next time.

---

### Post by mastablasta on 2011-10-10
try mintbackup tool. it's much easier to use. there are only 4 buttons. one for files backup one for settings backup. thew other 2 buttons are used to restore the backups.

---

### Post by ktat on 2011-10-10
You might want to try [Clonezilla]("http://clonezilla.org/").

---

### Post by haqking on 2011-10-10
lots of areas on this subject 

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)

[https://help.ubuntu.com/community/DuplicityBackupHowto](https://help.ubuntu.com/community/DuplicityBackupHowto)

---

### Post by inameiname on 2011-10-14
Relinux is coming along fairly well. The developer has plans to tweak/add quite a bit in the very near future, so your issue may be addressed with it very soon.

If you want, you can add a ticket (feature request/help) on his main site, so you could possibly get your issue addressed. Here is the link:

[http://sourceforge.net/p/re-linux/tickets/](http://sourceforge.net/p/re-linux/tickets/)

By the way, here are a couple more threads/postings about relinux:

[http://lkubuntu.wordpress.com/2011/10/10/relinux-a-way-to-create-a-bootable-iso-out-of-your-system/](http://lkubuntu.wordpress.com/2011/10/10/relinux-a-way-to-create-a-bootable-iso-out-of-your-system/)

[http://ubuntuforums.org/showthread.php?t=1857376&highlight=relinux](http://ubuntuforums.org/showthread.php?t=1857376&highlight=relinux)

---

