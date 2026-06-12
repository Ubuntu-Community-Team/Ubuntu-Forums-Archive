---
title: "AutoMount my NTFS disks"
date: 2011-01-27
forum: General Help
---

### Post by baqar on 2011-01-27
Hey 
How shall i auto mount my NTFS disk. Every time i want to use the disk i had to click on it to mount it....
Since i am downloading some program to one of my NTFS disk so its makes me mad. To first mount it and then run the whole procedure again. Hope u understand guyz

---

### Post by ajgreeny on 2011-01-27
Install **ntfs-config** and use it to set the mount and permissions of your ntfs partition.

---

### Post by baqar on 2011-01-27
> **ajgreeny said:**
> Install **ntfs-config** and use it to set the mount and permissions of your ntfs partition.

But How please help :D

---

### Post by spuch on 2011-01-27
add this line to your /etc/fstab file:
/dev/"your ntfs partition" /"any empty folder" ntfs nosuid,noexec,nodev,fmask=011 0 0

resemble this:

/dev/sda3 /e ntfs nosuid,noexec,nodev,fmask=011 0 0

---

### Post by Morbius1 on 2011-01-27
[1] Run the following command to see how your system sees your partitions:
```
sudo blkid -c /dev/null
```You will get an output that looks something like this:
> /dev/sdc1: LABEL="BACKUP" UUID="66E4DC83E4DC56C1" TYPE="ntfs" [2] Make a home for your partition to live in. For example:
```
sudo mkdir /media/Data
```[3] Add a line to /etc/fstab:
```
/dev/sdc1 /media/Data ntfs defaults,nls=utf8,umask=007,uid=1000,gid=46 0 0
```[I]Note: there are a limitless number of variations of the above line. spuch's addition of fmask=011 for example will trun off the execute bit on all files for group and others. The line above is almost exactly the way Ubuntu itself would add the the line in fstab had you chosen to mount these partitions during the initial install. The only modification I made was to make you the owner of the mount point (uid=1000) just to give you a place to put your trash and in case you wanted to share them across your home network using nautilus-share.
[/I]
[4] Run the following command to check for errors and mount your partition:
```
sudo mount -a
```

---

### Post by Mark Phelps on 2011-01-27
In my experience, it is a BAD idea to automount NTFS partitions in the following cases:
1) The partition is an OS partition (for Vista or Win7)
2) The partition is mounted read-write

Doing this is asking for trouble.  One unclean dismount and your OS partition is then rendered unbootable.  And since you have to boot into it to run chkdsk to fix it, you've now lost access to your MS Windows installation.

Much better approach is to have your shared data in an NTFS data partition.  That way, if there is an unclean dismount, you can boot into MS Windows and run chkdsk to repair the filesystem.

---

### Post by baqar on 2011-01-29
> **Mark Phelps said:**
> In my experience, it is a BAD idea to automount NTFS partitions in the following cases:
1) The partition is an OS partition (for Vista or Win7)
2) The partition is mounted read-write

Doing this is asking for trouble.  One unclean dismount and your OS partition is then rendered unbootable.  And since you have to boot into it to run chkdsk to fix it, you've now lost access to your MS Windows installation.

Much better approach is to have your shared data in an NTFS data partition.  That way, if there is an unclean dismount, you can boot into MS Windows and run chkdsk to repair the filesystem.

Well u people are taking my thing wrong.... Well the scenerio is that i use torrent file which is located in my D: drive of windows and to restart my torrent i had to go to home and to media and then mound any of the drive......

---

