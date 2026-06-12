---
title: "Need to make an emergency back up"
date: 2010-05-30
forum: General Help
---

### Post by timfinley on 2010-05-30
So I was doing the update to 10.04 when a freak thunderstorm knocked out the power. I can no longer load onto ubuntu from the HDD. I have been told to either do an emergency back up using the 10.04 live disk. I am not sure what to do when it comes to that. I have also heard I can just repair the boot file on the HDD. I don't know how to do that either. I wouldn't mind I fresh install but I do not want to lose any of my data. Any suggestions?

---

### Post by Sef on 2010-05-30
Emergency back up like you described is that your files for your documents are backed up to another hard drive, flash drive, etc.

---

### Post by CharlesA on 2010-05-30
Boot off the livecd and copy your home directory to a flash drive or different hard drive.

---

### Post by efflandt on 2010-05-30
If you can boot to a live system from either 9.10 or 10.04 install CD, you could use that to tar and/or copy files and directories to USB memory or hard drive.

---

### Post by timfinley on 2010-05-30
> **CharlesA said:**
> Boot off the livecd and copy your home directory to a flash drive or different hard drive.
  How? I have an external HDD connected via USB but I haven't figured out the commands needed to transfer the files.

I have tried this command:

```
(cd /FROMHDD && tar -cvlpSf -. | (cd /TOHDD && tar -xpSf -))
```
 I got "Cannot open: No such file or dir" and "Cannot mkdir: Input/output error" on nearly every file. When I entered cd /TOHDD then ls no files transfered.

I also tried "mv /FROM /TO" to no avail.

Pretty stumped here.

---

### Post by CharlesA on 2010-05-30
Is the drive you want to get files off of shown in the places menu?

---

### Post by timfinley on 2010-05-30
> **CharlesA said:**
> Is the drive you want to get files off of shown in the places menu?

yes. The drives I want to get files from were automatically mounted. I unmounted the drive I want to transfer files to and mounted it as root. All commands have been executed as root.

---

### Post by JustinR on 2010-05-30
> **timfinley said:**
> yes. I unmounted the drive and mounted it as root. All commands have been executed as root.

You might want to try that again with something like rsync.

Copying files with root replaces all user file permissions with root. This could severely mess up your new system!

---

### Post by CharlesA on 2010-05-30
Have you tried running fsck on it when it is unmounted? There might be damage to the file system due to the power loss.

---

### Post by nerdopolis on 2010-05-30
On your line the part that says  /FROMHD and /TOHD are supposed to be changed by you.

For example, (It may be different in your case)
If I opened my Hard drive from my file manager, and it put it on /media/disk and it puts my external drive on /media/disk-1, I want to copy from /media/disk to /media/disk-1

so I would replace /FROMHD with /media/disk and TOHD with /media/disk-1
```
(cd  /media/disk && tar -cvlpSf -. | (cd  /media/disk-1 && tar -xpSf -))
```BTW: do you remeber the error message you get? perhaps we know a solution, before you make such a drastic move to reinstall. (but it is a good idea to back up your drive still).

Give me a moment to test if that command actually works.


EDIT: Nope. It does not seem to be working here. Do as **[JustinR]("http://ubuntuforums.org/member.php?u=944014")** said. use rsync similar to this, only you will have to change the paths below. You can usually get the full path of the drives by looking at the 'address bar' of the file manager.
```
sudo rsync -aAHX /path/to/source/drive /path/to/destination/drive 
```

In my above example I would run 
```
sudo rsync -aAHX /media/disk /media/disk-1  
```
Bear in mind that it might be different for you.

---

### Post by timfinley on 2010-05-30
> **nerdopolis said:**
> On your line the part that says  /FROMHD and /TOHD are supposed to be changed by you.

For example, (It may be different in your case)
If I opened my Hard drive from my file manager, and it put it on /media/disk and it puts my external drive on /media/disk-1, I want to copy from /media/disk to /media/disk-1

so I would replace /FROMHD with /media/disk and TOHD with /media/disk-1
```
(cd  /media/disk && tar -cvlpSf -. | (cd  /media/disk-1 && tar -xpSf -))
```BTW: do you remeber the error message you get? perhaps we know a solution, before you make such a drastic move to reinstall. (but it is a good idea to back up your drive still).

Give me a moment to test if that command actually works.


EDIT: Nope. It does not seem to be working here. Do as **[JustinR]("http://ubuntuforums.org/member.php?u=944014")** said. use rsync similar to this, only you will have to change the paths below. You can usually get the full path of the drives by looking at the 'address bar' of the file manager.
```
sudo rsync -aAHX /path/to/source/drive /path/to/destination/drive 
```

Yes I know to replace /FROM and /TO, it is just easier to type that it. It would be /media/long line of numbers to /mnt. I will try rsync. Should I have the destination HDD mounted as root? I will try it not mounted as root. I usually get permission denied error, but wiht sudo I might get lucky.

Ok after trying these are the errors i get:

```
root@ubuntu:~# sudo rsync -aAHX /media/f2416d0b-62b7-447c-affa-0f2a317713e1 /media/Toshiba
rsync: mkstemp "/media/Toshiba/f2416d0b-62b7-447c-affa-0f2a317713e1/.dscn0187.jpg.ZTUo6W" failed: Input/output error (5)
rsync: recv_generator: mkdir "/media/Toshiba/f2416d0b-62b7-447c-affa-0f2a317713e1/.Trash-1000/expunged" failed: Input/output error (5)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/Toshiba/f2416d0b-62b7-447c-affa-0f2a317713e1/.Trash-1000/files" failed: Input/output error (5)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/Toshiba/f2416d0b-62b7-447c-affa-0f2a317713e1/.Trash-1000/info" failed: Input/output error (5)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/Toshiba/f2416d0b-62b7-447c-affa-0f2a317713e1/Capitalism.A.Love.Story.TS.XVID.2009" failed: Input/output error (5)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/Toshiba/f2416d0b-62b7-447c-affa-0f2a317713e1/Crossroads_1986_DVDrip_XviD~Ekolb" failed: Input/output error (5)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/Toshiba/f2416d0b-62b7-447c-affa-0f2a317713e1/Garden.State.2004.DvdRip.Xvid.ALLiANCE" failed: Input/output error (5)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/Toshiba/f2416d0b-62b7-447c-affa-0f2a317713e1/Its Always Sunny In Philadelphia" failed: Input/output error (5)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/Toshiba/f2416d0b-62b7-447c-affa-0f2a317713e1/Its.Always.Sunny.In.Philadelphia.S05E05.WS.PDTV.XviD-SYS" failed: Input/output error (5)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/Toshiba/f2416d0b-62b7-447c-affa-0f2a317713e1/Movies" failed: Input/output error (5)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/Toshiba/f2416d0b-62b7-447c-affa-0f2a317713e1/Primer" failed: Input/output error (5)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/Toshiba/f2416d0b-62b7-447c-affa-0f2a317713e1/[History Channel] Modern Marvels_Nikola Tesla-Mad Electricity" failed: Input/output error (5)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/Toshiba/f2416d0b-62b7-447c-affa-0f2a317713e1/lost+found" failed: Input/output error (5)
*** Skipping any contents from this failed directory ***
rsync: mkstemp "/media/Toshiba/f2416d0b-62b7-447c-affa-0f2a317713e1/.ophcrack-xp-livecd-2.3.1.iso.0oHuFo" failed: No such file or directory (2)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]
root@ubuntu:~# 


```

---

### Post by nerdopolis on 2010-05-30
Try running a disk check. It seems some files are unreadable. You will need to unmount your hard disk. Before you unmount, find the device file of your internal hard drive by running
```
df /path/to/mounted/drive
```

It might return something like /dev/sda1 or something, but in your case it seems like it might return a bunch of numbers...

write down or copy what comes up under the Filesystem column. Then unmount the file system with the file manager. 

then run 
```
sudo fsck -pv /path/returned 
```
to check the drive.

PS:
If it prompts you about a mounted FS, do NOT continue. The unmount might have failed, and if you continue if it gives you that warning, it might cause damage. 

After that, try the rsync command again.

---

### Post by timfinley on 2010-05-30
I just had a thought. I have two HDD installed. One HDD is 200gigs and contains the ubuntu install. The other is 80gig slave drive I use for extra storage. Do you think it would be possible to install ubuntu onto the 80 gig slave and make the 200 gig the new slave? or maybe I can fix the boot file. This is the reason:

```
root@ubuntu:/media# sudo fsck -pv /dev/sdc1
fsck from util-linux-ng 2.17.2
Toshiba was not cleanly unmounted, check forced.
Error reading block 492026 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  

Toshiba: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)
root@ubuntu:/media# 


```I think my external is fried.

---

### Post by nerdopolis on 2010-05-31
It should be possible to backup there, if there is enough space.

I wouldn't say your external is fried however, it just has a file system error on it. (unless if the file system error is caused by a hardware failure...)

First, can you try ```
sudo sudo fsck -yv /dev/sdc1

``` instead?

Lastly, what error are you getting that's keeping you from booting? Its still a good idea to backup your data, but perhaps we know a fix to get you running again, without a reinstall.

---

### Post by timfinley on 2010-05-31
> **nerdopolis said:**
> It should be possible to backup there, if there is enough space.

I wouldn't say your external is fried however, it just has a file system error on it. (unless if the file system error is caused by a hardware failure...)

First, can you try ```
sudo sudo fsck -yv /dev/sdc1

``` instead?

Lastly, what error are you getting that's keeping you from booting? Its still a good idea to backup your data, but perhaps we know a fix to get you running again, without a reinstall.

Here is the error I get with with fsck

```
Error reading block 61047296 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 61047297 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Restarting e2fsck from the beginning...
fsck.ext2: No such file or directory while trying to open /dev/sdc1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


```

I don't get any errors, it just gets stuck on the ubuntu loading screen and is forever loading.

---

### Post by nerdopolis on 2010-05-31
Is your external formatted with ext2? I doubt it, but I don't know why fsck is treating it like a ext2 FS... Seems like you might want to backup your external as well.

Did you try booting your system in recovery mode? You can select recovery in the GRUB menu. (I think you have to hold shift to get the menu as the system boots to get the menu) Recovery mode will output the messages on the screen for better diagnosis, so you can report back what comes up here.

---

### Post by timfinley on 2010-06-01
> **nerdopolis said:**
> Is your external formatted with ext2? I doubt it, but I don't know why fsck is treating it like a ext2 FS... Seems like you might want to backup your external as well.

Did you try booting your system in recovery mode? You can select recovery in the GRUB menu. (I think you have to hold shift to get the menu as the system boots to get the menu) Recovery mode will output the messages on the screen for better diagnosis, so you can report back what comes up here.

Same thing happens in recovery mode. Never loads completely.

---

### Post by nerdopolis on 2010-06-07
Does any text come up in recovery mode? What does it freeze at, or Does it freeze at different things at different times?  How long do you usually wait for?

---

