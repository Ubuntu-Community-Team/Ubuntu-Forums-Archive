---
title: "Automount drives"
date: 2011-05-10
forum: General Help
---

### Post by layers on 2011-05-10
I want my other partition to be mounted at startup as another partition. So far, I just mount it manually with ```
sudo mount -t vfat -o umask=000 /dev/sda2 /media/here
```.

I am aware that I can modify a file somewhere, so that it automounts, but that is not exactly what I want. If I do that, the drive is not displayed as a drive in the Places menu. It is just mounted as a folder in /media. 

In Ubuntu, it was doing exactly what I wanted automatically - it mounts it at start up, and displays it as a separate drive.

How can I do this in X?

---

### Post by Morbius1 on 2011-05-10
Unmount the partition is you have it mounted:
```
sudo umount /media/here
```Edit /etc/fstab as root:
```
gksu gedit /etc/fstab
```Add the following line at the end of the file:
```
/dev/sda2 /media/here vfat utf8,umask=000,uid=1000 0 2
```[COLOR=Blue]*I've added a "uid=1000" ( making you the owner ) to the list which is really unnecessary since the umask=000 gives everyone access but it will allow you to have a place for your trash. You can remove that option is you want.*[/COLOR]
Now run the following command to test for errors and mount the new partition:
```
sudo mount -a
```It will show up on the desktop and in places since the mount point is in /media.

[COLOR=Blue]**EDIT: Sorry, I'm a dingbat. Didn't see you are using Xubuntu:**[/COLOR]

Now open up Thunar and go to Filesystem > Right click /media/here > Send to > Side Pane ( Create shortcut )

---

### Post by layers on 2011-05-10
Something interesting here: It did not appear in Places, nor on the Desktop.
As I pressed PrtSc, it asked me where to save it, and one of the Places if the drive.
And while I am given the option to upload the image to ImgShck, one of the Places is the drive.
[[IMG]http://img691.imageshack.us/img691/8599/screenshotpb.png[/IMG]](http://img691.imageshack.us/i/screenshotpb.png/)

---

### Post by Keith W on 2011-05-10
Sorry to barge in on this one but I am also using Xubuntu (11.04) and wish to automount two partitions on sdc.   I have added these two lines to fstab as per the above:
/dev/sdc1/BackupDW vfat utf8,unmask=000
/dev/sdc2/BackupKW vfat utf8,unmask=000

the partitions being BackupDW and BackupKW, but when I enter sudo mount -a I get this error message (twice):
mount: mount point vfat does not exist

I am pretty raw when it comes to Linux so can you advise where I am going wrong please.   If it helps, the two partitions are formatted to NTFS.

---

### Post by layers on 2011-05-10
OK, awesome. While I am happy like this, is there a way to make it look like "File System"? Because now it looks like Downloads, Music, etc. Also, it appears in their group, and I can't drag it to the above group.

---

### Post by layers on 2011-05-10
> **Keith W said:**
> Sorry to barge in on this one but I am also using Xubuntu (11.04) and wish to automount two partitions on sdc.   I have added these two lines to fstab as per the above:
/dev/sdc1/BackupDW vfat utf8,unmask=000
/dev/sdc2/BackupKW vfat utf8,unmask=000

the partitions being BackupDW and BackupKW, but when I enter sudo mount -a I get this error message (twice):
mount: mount point vfat does not exist

I am pretty raw when it comes to Linux so can you advise where I am going wrong please.   If it helps, the two partitions are formatted to NTFS.
You are saying vfat for an NTSF drive. You should say ntfs.
like here, point 4: [http://www.technixupdate.com/mount-ntfs-fat32-windows-drive-in-ubuntu/](http://www.technixupdate.com/mount-ntfs-fat32-windows-drive-in-ubuntu/)
Now, get out! :P

---

### Post by Morbius1 on 2011-05-10
> OK, awesome.  While I am happy like this, is there a way to make it look like "File  System"? Because now it looks like Downloads, Music, etc. Also, it  appears in their group, and I can't drag it to the above group.
That I do not know how to do, sorry.

---

### Post by Morbius1 on 2011-05-10
@Keith W:
The syntax for a line in fstab is:

device mount-point filetype options other-stuff

You have no mount point so the system thinks vfat is a mount point and I seriously doubt that /dev/sdc1/BackupDW is a device so I would suggest starting your own topic and provide the output of the following commands:
```
sudo blkid -c /dev/null
cat /etc/fstab
mount
```

---

### Post by layers on 2011-05-10
> **Morbius1 said:**
> That I do not know how to do, sorry.
Do you know how the two groups are called?

---

### Post by JKyleOKC on 2011-05-10
> **Keith W said:**
> Sorry to barge in on this one but I am also using Xubuntu (11.04) and wish to automount two partitions on sdc.   I have added these two lines to fstab as per the above:
/dev/sdc1/BackupDW vfat utf8,unmask=000
/dev/sdc2/BackupKW vfat utf8,unmask=000

the partitions being BackupDW and BackupKW, but when I enter sudo mount -a I get this error message (twice):
mount: mount point vfat does not exist

I am pretty raw when it comes to Linux so can you advise where I am going wrong please.   If it helps, the two partitions are formatted to NTFS.You need to put a space between "sdc1" and "/BackupDW" and similarly on the second line. Without that space, the program thinks the "Backup" mount point is actually part of the partition name.

---

### Post by Keith W on 2011-05-11
Sincere thanks to those kind folks who responded to my query in the middle of this thread.   Using bits of all the replies I managed to get it together.  Working nicely now.

---

