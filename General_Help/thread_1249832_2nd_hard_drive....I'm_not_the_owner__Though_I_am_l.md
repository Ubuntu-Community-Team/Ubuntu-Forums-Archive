---
title: "2nd hard drive....I'm not the owner???  Though I am logged in as admin?"
date: 2009-08-25
forum: General Help
---

### Post by dtrot55 on 2009-08-25
I put in a 2nd hard drive and I can not give it any permissions due to it saying that I don't own it? Any ideas??

[IMG]http://i103.photobucket.com/albums/m142/dtrot55/Screenshot-1.png[/IMG]

---

### Post by sailthesea on 2009-08-25
Is it preused? Maybe encrypted? Live session to mount and format it? SuperGrub?

---

### Post by Bachstelze on 2009-08-25
Paste the output of

```
mount
```

It will tell us where your drive is mounter, then we can proceed to giving you the correct permissions.

---

### Post by dtrot55 on 2009-08-25
dtrot@dtrot-ubuntu:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dtrot/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dtrot)
/dev/sdb1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

---

### Post by Bachstelze on 2009-08-25
Is it an internal or external drive? Also paste the output of

```
sudo fdisk -l
```

---

### Post by dtrot55 on 2009-08-25
It is an internal IDE hard drive...will do the code when i get home from work

---

### Post by b0b138 on 2009-08-25
This is the way it's supposed to be (I think lol)  Unlike windows, the idea is not to put things at the root of a drive, but to make subfolders.  And for security reasons, not to give anyone but root permission to the drive. Im assuming if you check the permissions of the Jessi_Backup, you'll find you are the owner of that and can read/write to that. If you want another folder, you'll need to do sudo mkdir /media/disk/new_folder  then change the permissions of that folder.

---

### Post by dtrot55 on 2009-08-25
Sounds like that makes sense...didn't think to try it...will do when i get home..thanks for the idea

---

### Post by dtrot55 on 2009-08-26
tried...got the same error :(

---

### Post by dtrot55 on 2009-08-26
Here are results of the code above:

dtrot@dtrot-ubuntu:~$ sudo fdisk -l
[sudo] password for dtrot: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x99b699b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19273   154810341   83  Linux
/dev/sda2           19274       19457     1477980    5  Extended
/dev/sda5           19274       19457     1477948+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x340033ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       20672   156280288+   7  HPFS/NTFS

---

### Post by amac777 on 2009-08-26
The drive is of type NTFS, which does not support linux permissions as far as I know.

However, from your screen shot in the original post, it looks like all users can read and write to that directory Jessi_Backup. So you should already have the ability to create or delete folders and files. You should also be able to rename it etc. Besides, changing permissions (which don't exist on NTFS), are you having problems working with files and directories?

---

### Post by dtrot55 on 2009-08-26
yeah i didnt see any format options like in windows you can just right click and say format and it will do it...but i dont see to have any issues with reading and writing to it...how would i go about getting it formatted for ubuntu?

---

### Post by amac777 on 2009-08-26
The program 'gparted' will allow you to reformat the drive for ext3, which is a common file system type for linux.

```
sudo apt-get install gparted
```

You should see it in SYSTEM->ADMINISTRATION->Partition editor

Make sure you read about how to use it first and be very sure you are re-partioning the right drive!!!! You could lose all your data if you format the wrong drive.

---

### Post by dtrot55 on 2009-08-26
installed gparted...formatted correct drive to ext3...now it says this

[IMG]http://i103.photobucket.com/albums/m142/dtrot55/Screenshot-2.png[/IMG]

---

### Post by dtrot55 on 2009-08-26
This hard drive is connected to a PCI IDE Controller that I put in becasue this computer only has 1 IDE port for CDRoms....would that have something to do with it?

---

### Post by amac777 on 2009-08-26
I think your PCI IDE controller is working fine because so far things are behaving as expected. 

By default, regular users don't have permissions to a freshly formated drive, to get permissions on that drive for your current user, you can either set the whole drive to be owned by your user: (replace your-user-name with your whatever username you use to login)

```
sudo chown your-user-name:your-user-name /media/Backup
```

Then you will be able to create directories and set permsissions on /media/Backup from your regular user.

Or you can create a directory off the root of that drive and then give your user permissions to do anything within that directory:

```
sudo mkdir /media/Backup/some-directory
sudo chown your-user-name:your-user-name /media/Backup/some-directory
```

All this probably seems not so obvious right now, but after you get used to permissions, it should come more natural.

---

### Post by dtrot55 on 2009-08-27
That's really kind of a pain seeing as I am the only user on the machine and the admin...so why can't it default to that? I could understand if i had like 20 users...but just seems like a added annoyance....though thank you for clearing all that up.

---

### Post by amac777 on 2009-08-27
It's a security feature. Even though your regular user can have "admin" priveledges when needed by using sudo, if you don't use sudo, you are still a regular user and cannot modify files for which your user does not have permission. This will stop you from doing something to your system that you shouldn't be doing. It would also stop any malware or unauthorized person who gets access to your account from doing something to your system that they shouldn't be doing.

---

