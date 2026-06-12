---
title: "Need som help with testdisk copying"
date: 2009-10-25
forum: General Help
---

### Post by espentf on 2009-10-25
Hi
Some days ago my external WD My Book 1terra decided to quit on me. After trying several programs i came across Testdisk. With it I managed to see my files and copy them.
The only problem is that i can only copy them to a directory that doesnt seem to exist.
When I'm on the copy screen I can choose where I want to copy my files to but for example under the home directory there is no users, only the folder Users, wich is empty.
I run testdisk from Gparted live disk because i could'nt manage to install it on Ubunt. It seems like it want me to copy my files to the directory Gparted loads, and not the disk i want it to. 
When I am done copying a file it says its complete and I dont get any error messenges, however when i look at my disk afterwords, no files where copyed to the desired disk.

I would be most grateful if anyone could help me with my little problem.

Espentf

---

### Post by P4man on 2009-10-25
first of all make VERY sure you are not copying the recovered files back to the same drive. 

The drive you want to copy them to should be mounted. If you want to copy them to your internal drive, go there first (places  > nameofyourdisk)

It should automatically mount in /media/nameofyourdisk or /mnt/nameofyourdisk, im not sure.

After doing that start testdisk you should be able to browse to 
/media/yourdisk/home/yourusername

(media could also be mnt)

save m there.

BTW, doing it from a livecd is the best approach.

---

### Post by espentf on 2009-10-26
thanks for the help.

So it turns out the disk i want to copy to was not mounted.
I try to mount it with the terminal on the Gparted live cd however when i try to mount it with the command
sudo mount /dev/hda1
i get the error:
mount: can't find /dev/hda1 in /etc/fstab or /etc/mtab

can anyone help with the mounting in terminal?
btw my disks path is /dev/hda1, but how do i find out the name?

---

### Post by P4man on 2009-10-26
/**dev**/hda1 is the device, its not a mounted readable or writeable filesystem. After mounting it, the filesystem will be accessible through /mnt/mountpoint
(btw are you sure its hda and not sda? Are you using an old version of ubuntu perhaps?)

Anyway, is that disk a ntfs or linux partition?  Most partitions will mount automatically if you access them from the places menu or in nautilus file manager. If thats not the case, or if you're using an older version of ubuntu,  please provide the output of

```
sudo fdisk -l
```

---

### Post by espentf on 2009-10-26
Thank you for the reply, this is the first time I'm using linux so bare with me.

In the GParted window the file system of the HD is ext3 but in terminal with the fdisk -l command it says that the system is linux. I dont know what any of that means.
And i am positive its /dev/hda( that what it says on the top of the Gparted window), don't know what ubuntu verson the computer i running but atm i am using the GParted live cd.

---

### Post by P4man on 2009-10-26
Ext3 is a native linux filesystem, like ntfs or FAT32 is for windows.
Ok Im guessing you're using a fairly old livecd, but lets do it manually then. Open a terminal from applications > accessories

Then lets make a mountpoint.

```
sudo mkdir /mnt/myharddisk
```
Then lets make sure you own that mountpoint. so you can read and write to it. ubuntu should be your current username so type
```
sudo chown ubuntu /mnt/myharddisk
```

then lets mount your harddrive there

```
sudo mount /dev/hda1 /mnt/myharddisk/
```

see if you can browse it. Go to places in the main menu. If you dont see it there, select any folder to open nautilus file manager. then click "filesystem" in the left hand pane. Browse to /mnt/myharddisk. Then continue to /mnt/myharddisk/home/yourusername

Check if you can read it. check if you can write by creating a new folder where you want to recover your files. If that works, go ahead in testdisk and save your files to the above path.

---

### Post by espentf on 2009-10-26
Thank you so much for the help p4man the mount worked excellently, and i am now able to copy my files;)

---

