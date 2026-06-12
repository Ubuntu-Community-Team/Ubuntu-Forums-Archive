---
title: "Mounting second drive within file system"
date: 2011-06-09
forum: General Help
---

### Post by PendragonUK on 2011-06-09
I have two hard drives in my desktop, a 250GB and 500GB.

The first drive has the swap and / the second drive is just sat there having to be mounted before use. I have a half remembered thought that the second drive could be given a mount point within the file system. I have often partitioned drives so that / is septate to /home but not over different phisical drives. I wouldn't want the 500GB to be /home because a large chunk of the 250GB would not normally be used.

What I would like is to have the first drive set 20GB / the rest to /home. Then the 500GB set to /home/data so it would apear within the home directory or even better /home/*user*/data as I'm the only user of the computer.

Secondary question, would there be any advantage of putting the swap on the second drive? right at the outer edge short stroking??

---

### Post by MSPdwalt on 2011-06-09
Well...I'm a little lost as far as what you're trying to do.  A df -h output would help us understand how you're currently setup.

Also an fdisk -l for each drive would be handy too.

---

### Post by seawolf167 on 2011-06-09
Just to make sure I'm understanding you correctly, you want to have your 2nd physical hard drive mounted automatically at the place listed in your post, correct?

If so, you'll want to add an /etc/fstab entry. If you want to work through it yourself, you can click the fstab link in my signature, please post the output of the below commands for us to help you:

```
sudo fdisk -l
mount
sudo blkid
```Placing swap on the 2nd drive would speed things up *a tiny bit* only if your computer routinely accesses the swap space.

---

### Post by PendragonUK on 2011-06-09
The output from df -h

```
stevem@stevem-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             227G   16G  200G   8% /
none                  494M  716K  494M   1% /dev
none                  501M  1.3M  500M   1% /dev/shm
none                  501M  360K  500M   1% /var/run
none                  501M     0  501M   0% /var/lock
/dev/sdb1             459G  137G  299G  32% /media/Data
df: `/root/.gvfs': Permission denied

```

There are two phisical drives, I would like the second, larger drive to mount within the file system of the first smaller one. So when looking in my user directory the drive would behave like a directory. When we format our drives when installing we select the mount point (/,  /home, /var, /tmp, etc) I would like to set the mount point of the second drive to be /home/*user*/data in my case /home/stevem/data.

---

### Post by PendragonUK on 2011-06-09
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00046432

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30028   241193984   83  Linux
/dev/sda2           30028       30402     3002369    5  Extended
/dev/sda5           30028       30402     3002368   82  Linux swap / Solaris

Disk /dev/sdb: 500.0 GB, 499971544064 bytes
255 heads, 63 sectors/track, 60784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8969a6e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60784   488247448+  83  Linux
stevem@stevem-desktop:~$ 

```

---

### Post by seawolf167 on 2011-06-09
You didn't post the output of 

```
sudo blkid
```so we'll have to use /dev/sdXY versus the drive UUIDs, and start with a guess that it is formatted in ext4:

Add the mount point

```
mkdir ~/data
```Open /etc/fstab for editing

```
sudo gedit /etc/fstab
```Add the following line at the bottom, save the file and quit

```
#Entry for /dev/sdb1
/dev/sdb1     /home/stevem/data      ext4     defaults     0     2
```The logoff and logback in (or restart), check to ensure it is mounted correctly

---

### Post by PendragonUK on 2011-06-09
I had a look at the link in your sig and installed PySDM, and managed to get it sorted... 

I have a directory called Data within my /home*/user* directory and when I look in it I see the contents of the second large hard drive.

This is what I had wanted to acheave.

Thanks for your help I can put this one down as solved :)

---

### Post by seawolf167 on 2011-06-09
Easy enough, glad its working!

If in the future you want to add NTFS drives automatically, the tool I suggest it NTFSConfig

```
sudo apt-get install ntfsconfig
```

---

