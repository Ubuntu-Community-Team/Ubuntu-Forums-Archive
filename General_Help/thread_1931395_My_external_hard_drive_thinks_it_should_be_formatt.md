---
title: "My external hard drive thinks it should be formatted."
date: 2012-02-25
forum: General Help
---

### Post by S3V3NTiNiN3 on 2012-02-25
Hi,

I made a very stupid mistake and deleted the .Trash1000 and $RECYCLEBIN on my new external hard drive after transferring loads of files to it. Now whenever I plug it in, two different operating systems (Win7 and elementary) are both telling me it needs to be formatted. I don't want to lose all my data - is there any way around this situation?

Thanks.

---

### Post by cariboo on 2012-02-25
Moved to General Help, as this is a support question.

---

### Post by WasMeHere on 2012-02-25
Hi and welcome to the Ubuntu Forums!

What operating system are you running now? If you have no Ubuntu installation CD or USB drive, can you download an iso file? What computer are you running? If you describe these things, we can help you find some way to repair your external drive. Is is a USB or eSATA hard disk drive?

If the only problem is that the trashcans are deleted, it should be fairly easy to restore the drive using Windows to restore $RECYCLEBIN and some linux distro to restore .Trash1000.

Have fun finding out
Olle

---

### Post by sudodus on 2012-02-25
The OS wants you to format it, but can you see it somehow?

1. With a file browser (like Explorer)?

2. Are you familiar with the command line terminal? Can you run the command (if you have linux)
```
sudo fdisk -lu
```
and
```
df
``` and post the code in a reply in this thread? If not, please ask what you need!

---

### Post by S3V3NTiNiN3 on 2012-02-25
Thank you, both, for your help.

The hard drive still does not work on Windows 7, but my main computer, which is running elementary (soon to make the move to Debian, but that is something I cannot accomplish without a working external hard drive to transfer my files to!) has suddenly begun recognizing it. Now, however, a new problem has surfaced:

Screen Capture I:  [http://fall.rain.cl/Miscellaneous/1.png](http://fall.rain.cl/Miscellaneous/1.png)
Screen Capture II: [http://fall.rain.cl/Miscellaneous/2.png](http://fall.rain.cl/Miscellaneous/2.png)

This one has me stumped. Any suggestions?

---

### Post by sudodus on 2012-02-25
> **S3V3NTiNiN3 said:**
> Thank you, both, for your help.

The hard drive still does not work on Windows 7, but my main computer, which is running elementary (soon to make the move to Debian, but that is something I cannot accomplish without a working external hard drive to transfer my files to!) has suddenly begun recognizing it. Now, however, a new problem has surfaced:

Screen Capture I:  [http://fall.rain.cl/Miscellaneous/1.png](http://fall.rain.cl/Miscellaneous/1.png)
Screen Capture II: [http://fall.rain.cl/Miscellaneous/2.png](http://fall.rain.cl/Miscellaneous/2.png)

This one has me stumped. Any suggestions?
I: What folder did you try to create? Do you have permissions to do it; maybe you should do it with superuser (administrator) privileges.
II: You have the windows recycle bin, but not the linux .Trash-1000, and maybe the system doesn't want to trash it somewhere else. Or is this also a permissions issue?

How is the drive mounted? Is it read/write or read-only?

---

### Post by S3V3NTiNiN3 on 2012-02-25
> **sudodus said:**
> I: What folder did you try to create? Do you have permissions to do it; maybe you should do it with superuser (administrator) privileges.
II: You have the windows recycle bin, but not the linux .Trash-1000, and maybe the system doesn't want to trash it somewhere else. Or is this also a permissions issue?

How is the drive mounted? Is it read/write or read-only?

I tried to create a test directory for purposes of generating the message, but the same message comes up every time, no matter what the name of the directory. I do have permissions to create directories; or, rather, I should have - I have not been changing any permissions on that drive.

Wouldn't the .Trash-1000 file be hidden in the graphical interface, considering the fact that it is a dot-file?

Again, regarding the drive mounting, it should be read-write as I have not changed any permissions.

Thank you for your help! :)

---

### Post by sudodus on 2012-02-26
So you should have read and write permissions on the external HDD. I guess you can read and write without problems on your internal drive.

I guess your browser can be set to either show or hide .files. Does your reply mean that you have made a .Trash-1000 directory?

Maybe you can check the permissions of the external HDD 'E' from a command line terminal window. Are you familiar with that? For example, ***cd*** changes the directory and the command ***ls*** will list files and subdirectories of the current directory similar to ***dir*** in a Windows dosprompt window.

Try this command (or something similar)
```
cd /media/E
``` to 'go to' the external HDD 'E' and the following command to list the files and their permissions.
```
ls -la
```
It would help if you can post the output of this last command, when the current directory is 'E'.

---

### Post by S3V3NTiNiN3 on 2012-02-26
> **sudodus said:**
> So you should have read and write permissions on the external HDD. I guess you can read and write without problems on your internal drive.

I guess your browser can be set to either show or hide .files. Does your reply mean that you have made a .Trash-1000 directory?

Maybe you can check the permissions of the external HDD 'E' from a command line terminal window. Are you familiar with that? For example, ***cd*** changes the directory and the command ***ls*** will list files and subdirectories of the current directory similar to ***dir*** in a Windows dosprompt window.

Try this command (or something similar)
```
cd /media/E
``` to 'go to' the external HDD 'E' and the following command to list the files and their permissions.
```
ls -la
```
It would help if you can post the output of this last command, when the current directory is 'E'.

Yes, the internal drive works flawlessly.

I did try at one point, but I'm not sure if I did it correctly. Now it will not allow me to do anything, though.

Command output:

```
lawrence@Dawn:~$ cd /media/E
lawrence@Dawn:/media/E$ ls -la
total 116384
drwx------ 1 lawrence lawrence      4096 2012-02-04 17:09 .
drwxr-xr-x 3 root     root          4096 2012-02-26 01:24 ..
-rw------- 3 lawrence lawrence 119164928 2012-02-04 17:09 debian-6.0.4-i386-netinst.iso
drwx------ 1 lawrence lawrence      4096 2012-02-25 13:30 Music
drwx------ 1 lawrence lawrence         0 2012-02-04 10:24 $RECYCLE.BIN
drwx------ 1 lawrence lawrence         0 2012-02-25 13:30 .Trash-1000
drwx------ 1 lawrence lawrence         0 2012-01-29 08:02 Video
lawrence@Dawn:/media/E$ 

```

---

### Post by sudodus on 2012-02-26
> **S3V3NTiNiN3 said:**
> Yes, the internal drive works flawlessly.

I did try at one point, but I'm not sure if I did it correctly. Now it will not allow me to do anything, though.

Command output:

```
lawrence@Dawn:~$ cd /media/E
lawrence@Dawn:/media/E$ ls -la
total 116384
drwx------ 1 lawrence lawrence      4096 2012-02-04 17:09 .
drwxr-xr-x 3 root     root          4096 2012-02-26 01:24 ..
-rw------- 3 lawrence lawrence 119164928 2012-02-04 17:09 debian-6.0.4-i386-netinst.iso
drwx------ 1 lawrence lawrence      4096 2012-02-25 13:30 Music
drwx------ 1 lawrence lawrence         0 2012-02-04 10:24 $RECYCLE.BIN
drwx------ 1 lawrence lawrence         0 2012-02-25 13:30 .Trash-1000
drwx------ 1 lawrence lawrence         0 2012-01-29 08:02 Video
lawrence@Dawn:/media/E$ 

```
I have the same permissions on a trashcan on a USB stick, so it should be OK. We have to look somewhere else.

- Can you read files (so that it would be possible to backup the content of your external drive)?

- Can you write a file (or is it the same problem as creating a directory or deleting a file)? Try creating a file with a terminal command
```
cd /media/E
echo 'Hello World' > hello.txt
```

Please post the output of
```
sudo fdisk -lu
``` and of
```
cat /etc/mtab
```
fdisk shows information about drives and partitions and mtab contains information about the mounted devices.

If it would be recognized by Windows, consider using ***chkdsk /f*** from Windows! But to get there we need another option. Try to run ***testdisk*** to check and repair your external HDD. Browse the internet to read about testdisk! It can be installed into linux or you can download an iso file and make a boot CD or USB drive as listed at
[[COLOR="Red"]_http://www.cgsecurity.org/wiki/TestDisk_Livecd_[/COLOR]]("http://www.cgsecurity.org/wiki/TestDisk_Livecd")

---

### Post by S3V3NTiNiN3 on 2012-02-26
> **sudodus said:**
> I have the same permissions on a trashcan on a USB stick, so it should be OK. We have to look somewhere else.

- Can you read files (so that it would be possible to backup the content of your external drive)?

- Can you write a file (or is it the same problem as creating a directory or deleting a file)? Try creating a file with a terminal command
```
cd /media/E
echo 'Hello World' > hello.txt
```

Please post the output of
```
sudo fdisk -lu
``` and of
```
cat /etc/mtab
```
fdisk shows information about drives and partitions and mtab contains information about the mounted devices.

If it would be recognized by Windows, consider using ***chkdsk /f*** from Windows! But to get there we need another option. Try to run ***testdisk*** to check and repair your external HDD. Browse the internet to read about testdisk! It can be installed into linux or you can download an iso file and make a boot CD or USB drive as listed at
[[COLOR="Red"]_http://www.cgsecurity.org/wiki/TestDisk_Livecd_[/COLOR]]("http://www.cgsecurity.org/wiki/TestDisk_Livecd")

The files open successfully, yes, but I'm not sure if I have another hard drive with any space on it to back the files up to. I will check into that.

In regards to whether I can create a file with Terminal, it appears to have the same problem as the graphical interface method:

```
lawrence@Dawn:~$ cd /media/E
lawrence@Dawn:/media/E$ echo 'hello world' > hello.txt
bash: hello.txt: Input/output error
lawrence@Dawn:/media/E$ 

```

sudo fdisk -lu output:

```
lawrence@Dawn:~$ cd /media/E
lawrence@Dawn:/media/E$ sudo fdisk -lu
[sudo] password for lawrence: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004197b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   964485119   482241536   83  Linux
/dev/sda2       964487166   976771071     6141953    5  Extended
/dev/sda5       964487168   976771071     6141952   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7bf32e13

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768127   488384032+   7  HPFS/NTFS
lawrence@Dawn:/media/E$ 

```

cat /etc/mtab output:

```
lawrence@Dawn:~$ cd /media/E
lawrence@Dawn:/media/E$ cat /etc/mtab
/dev/sda1 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/lawrence/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=lawrence 0 0
/dev/sdb1 /media/E fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
lawrence@Dawn:/media/E$ 

```

I don't have access to the computer running Windows at the moment, as someone else is using it - but as soon as I do I will try chkdsk /f. Does that command provide an output I should post here?

---

### Post by sudodus on 2012-02-26
> **S3V3NTiNiN3 said:**
> ...
I don't have access to the computer running Windows at the moment, as someone else is using it - but as soon as I do I will try chkdsk /f. Does that command provide an output I should post here?
Yes, it might be interesting if it indicates some errors. It is possible to mark, cut and paste in a dos-prompt window, but if you don't find it out, you can make alt + PrtScrn and attach a picture.

I'll be back if I find something else in your latest post ...

---

### Post by S3V3NTiNiN3 on 2012-02-26
> **sudodus said:**
> Yes, it might be interesting if it indicates some errors. It is possible to mark, cut and paste in a dos-prompt window, but if you don't find it out, you can make alt + PrtScrn and attach a picture.

I'll be back if I find something else in your latest post ...

Thank you so much for all of your help. I am sincerely greatful.

---

### Post by sudodus on 2012-02-26
> **S3V3NTiNiN3 said:**
> The files open successfully, yes, but I'm not sure if I have another hard drive with any space on it to back the files up to. I will check into that.

In regards to whether I can create a file with Terminal, it appears to have the same problem as the graphical interface method:

```
lawrence@Dawn:~$ cd /media/E
lawrence@Dawn:/media/E$ echo 'hello world' > hello.txt
bash: hello.txt: Input/output error
lawrence@Dawn:/media/E$ 

```
I was afraid that it was like that, and now we know. It is a general problem, that the filesystem does not allow writing, although ls -l indicates that is has write permission.
> 
sudo fdisk -lu output:

```
lawrence@Dawn:~$ cd /media/E
lawrence@Dawn:/media/E$ sudo fdisk -lu
[sudo] password for lawrence: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004197b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   964485119   482241536   83  Linux
/dev/sda2       964487166   976771071     6141953    5  Extended
/dev/sda5       964487168   976771071     6141952   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7bf32e13

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768127   488384032+   7  HPFS/NTFS
lawrence@Dawn:/media/E$ 

```
I see nothing wrong in the output of fdisk.
> 
cat /etc/mtab output:

```
lawrence@Dawn:~$ cd /media/E
lawrence@Dawn:/media/E$ cat /etc/mtab
/dev/sda1 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/lawrence/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=lawrence 0 0
[COLOR="Red"]/dev/sdb1 /media/E fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0[/COLOR]
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
lawrence@Dawn:/media/E$ 

```
Also mtab indicates that the partition sdb1 is mounted read/write, but for some reason it is not. [COLOR="Red"]There are gurus around at the Ubuntu Forums. Maybe one of them can see or guess what is wrong[/COLOR]. Otherwise I suggest that you make a backup (copying all the files with ***cp*** or ***rsync*** should do it). And then try with ***testdisk***. If that does not work, repartition, reformat and let us hope that the drive is running again.

Finally: Have you checked the S.M.A.R.T. status of the drive. It can be done with ***palimpsest***. If you don't find it, install with
```
sudo apt-get install gnome-disk-utility
```

---

### Post by audiomick on 2012-02-26
Just a quick comment on an earlier question that I don't think got answered.

Yes, the .trash folder will be hidden. It can be viewed in your file browser by choosing to show hidden files.

Further, in my experience that folder always appears automatically as soon as a drive is mounted to a Linux system or to a Mac. You can erase it as often as you like. It will be there again when you mount the drive to Linux again.

---

### Post by S3V3NTiNiN3 on 2012-02-26
> **audiomick said:**
> Just a quick comment on an earlier question that I don't think got answered.

Yes, the .trash folder will be hidden. It can be viewed in your file browser by choosing to show hidden files.

Further, in my experience that folder always appears automatically as soon as a drive is mounted to a Linux system or to a Mac. You can erase it as often as you like. It will be there again when you mount the drive to Linux again.

Thank you for clarifying that. :)

> **sudodus said:**
> I was afraid that it was like that, and now we know. It is a general problem, that the filesystem does not allow writing, although ls -l indicates that is has write permission.

I see nothing wrong in the output of fdisk.

Also mtab indicates that the partition sdb1 is mounted read/write, but for some reason it is not. [COLOR="Red"]There are gurus around at the Ubuntu Forums. Maybe one of them can see or guess what is wrong[/COLOR]. Otherwise I suggest that you make a backup (copying all the files with ***cp*** or ***rsync*** should do it). And then try with ***testdisk***. If that does not work, repartition, reformat and let us hope that the drive is running again.

Finally: Have you checked the S.M.A.R.T. status of the drive. It can be done with ***palimpsest***. If you don't find it, install with
```
sudo apt-get install gnome-disk-utility
```

I suppose I will back things up, then, if I have enough hard drive space.

Here is palimsest (Gnome Disk Utility)'s report on the drive:

[http://fall.rain.cl/Miscellaneous/e-palimpsest.png](http://fall.rain.cl/Miscellaneous/e-palimpsest.png)

---

### Post by sudodus on 2012-02-26
> **S3V3NTiNiN3 said:**
> 
I suppose I will back things up, then, if I have enough hard drive space.

Here is palimsest (Gnome Disk Utility)'s report on the drive:

[http://fall.rain.cl/Miscellaneous/e-palimpsest.png](http://fall.rain.cl/Miscellaneous/e-palimpsest.png)
Good, the disk is healthy, which means no bad sectors, which cannot be read or written.

Yes, it is a good idea to back everything up. Maybe you can borrow an external drive temporarily from a friend or colleague.

---

