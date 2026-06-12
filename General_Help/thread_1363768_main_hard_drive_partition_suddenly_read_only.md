---
title: "main hard drive partition suddenly read only"
date: 2009-12-24
forum: General Help
---

### Post by keevill on 2009-12-24
Suddenly my laptop's main file storage partition is read only. Even logging is as root and executing chmod -R 755 <partition name> just produces a host of error messages 'read only file system'.
Help from someone please 

Output of cat /etc/fstab


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                               0  0  
# / was on /dev/sda1 during installation
UUID=2c11c4ed-6c5c-4e5c-8767-30dac980e405  /              ext2         relatime,errors=remount-ro             0  1  
# swap was on /dev/sda5 during installation
UUID=918c8a62-eb93-4f42-93b0-de940fabd9eb  none           swap         sw                                     0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8                  0  0  
# For USB access with Virtualbox
none                                       /proc/bus/usb  usbfs        devgid=124,devmode=664                 0  0  
/dev/sda2                                  /media/sda2    ntfs         nls=iso8859-1,ro,users,umask=000,user  0  0  
192.168.0.222:/gtt_general /mnt/snapserver nfs defaults 0 0

---

### Post by Some Penguin on 2009-12-24
> **keevill said:**
> Suddenly my laptop's main file storage partition is read only. Even logging is as root and executing chmod -R 755 <partition name> just produces a host of error messages 'read only file system'.
Help from someone please 

UUID=2c11c4ed-6c5c-4e5c-8767-30dac980e405  /              ext2         relatime,errors=remount-ro             0  1  


See that 'errors=remount-ro'?  You've told it to mount the filesystem read-only when there are problems, which is probably what it is doing.  Find and fix them.  e2fsck will likely come in handy.

---

### Post by lmarmisa on 2009-12-24
[I]# / was on /dev/sda1 during installation
UUID=2c11c4ed-6c5c-4e5c-8767-30dac980e405  /              ext2         relatime,errors=remount-ro             0  1

[/I]Apparently your system is detecting some errors in your hard disk drive and, according to this line of the /etc/fstab file, the partition is remounted in read only mode.

[http://ubuntuforums.org/showthread.php?t=315850](http://ubuntuforums.org/showthread.php?t=315850)

Best regards,

Luis

---

### Post by keevill on 2009-12-24
> **Some Penguin said:**
> See that 'errors=remount-ro'?  You've told it to mount the filesystem read-only when there are problems, which is probably what it is doing.  Find and fix them.  e2fsck will likely come in handy.

When I try to run that command on the partition and after the error below, try to run it on a sub directory, I get the errors .
Pls see below and thank you for trying to assist me
-keevill-

davidvaio@davidvaio-laptop:/media$ sudo e2fsck -p sda2
[sudo] password for davidvaio: 
e2fsck: Is a directory while trying to open sda2
sda2: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>



davidvaio@davidvaio-laptop:/media$ cd sda2
davidvaio@davidvaio-laptop:/media/sda2$ ls
aa1 software               domain tools       New Folder
acer drivers               Link to pix        oct iphone pics
audiobooks                 Maxprog            pix
backup                     movies             WER47C9.tmp.version.txt
Bluetooth Exchange Folder  My Data Sources    wmsetup.log
CaptureWiz                 my documents
ClipCache                  My Received Files


davidvaio@davidvaio-laptop:/media/sda2$ sudo e2fsck -p pix
e2fsck: Is a directory while trying to open pix
pix: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

davidvaio@davidvaio-laptop:/media/sda2$

---

### Post by bodhi.zazen on 2009-12-25
/dev/sda2 is a ntfs drive, so chown and chmod do not work on ntfs.

In fstab you have ro and a umask value, remove the ro and see if that helps.

If not, then your ntfs file system is probably corrupt. IMO best to boot to windows and allow windows to fix the problem.

If you no longer run windows, I suggest you also give up on NFTS as linux tools are no so great.

You can try ntfsfix /dev/sda2

Be sure to unmount the partition first =)

---

### Post by keevill on 2009-12-25
> **bodhi.zazen said:**
> /dev/sda2 is a ntfs drive, so chown and chmod do not work on ntfs.

In fstab you have ro and a umask value, remove the ro and see if that helps.

If not, then your ntfs file system is probably corrupt. IMO best to boot to windows and allow windows to fix the problem.

If you no longer run windows, I suggest you also give up on NFTS as linux tools are no so great.

You can try ntfsfix /dev/sda2

Be sure to unmount the partition first =)

I no longer use Windows but how can I get rid of NTFS without losing my data?
I removed the ro and also tried the ntfsfix suggestion but still only read access.
Here's the amended fstab file if that gives a further clue to a solution.


'# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                               0  0
# / was on /dev/sda1 during installation
UUID=2c11c4ed-6c5c-4e5c-8767-30dac980e405  /              ext2         relatime,errors=remount-ro             0  1
# swap was on /dev/sda5 during installation
UUID=918c8a62-eb93-4f42-93b0-de940fabd9eb  none           swap         sw                                     0  0
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8                  0  0
# For USB access with Virtualbox
none                                       /proc/bus/usb  usbfs        devgid=124,devmode=664                 0  0
/dev/sda2                                  /media/sda2    ntfs         nls=iso8859-1,users,umask=000,user  0  0
192.168.0.222:/gtt_general /mnt/snapserver nfs defaults 0 0

---

### Post by bodhi.zazen on 2009-12-26
> **keevill said:**
> I no longer use Windows but how can I get rid of NTFS without losing my data?

You have to copy all the data to another location, either another physical partition, CD, DVD, flash drive, reformat the partition to say ext4, then restore your data.

Seeing as the partition is ro and the Linux tools are not fixing it, no better time then the present =)

Hopefully somebody with more experience at fixing ntfs partitions from Linux can offer better advice.

---

### Post by keevill on 2009-12-26
> **bodhi.zazen said:**
> You have to copy all the data to another location, either another physical partition, CD, DVD, flash drive, reformat the partition to say ext4, then restore your data.

Seeing as the partition is ro and the Linux tools are not fixing it, no better time then the present =)

Hopefully somebody with more experience at fixing ntfs partitions from Linux can offer better advice.

OK that's not such a problem - thx for pointing me in the only sensible direction.
-keevill-

---

### Post by NFblaze on 2009-12-26
Wait a minute you do realize you ran the e2fsck on **sda2** which is the NTFS partition and not on **sda1** which is the EXT2 partition.

e2fsck is for EXT type partitions formats. Try it again with the correct partitions. If that doesnt work see if you can sudo nano from the terminal and remove errors=remount-ro. 


Also, if you get that working you can backup you stuff on the NTFS partiton by using the LiveCD and copying it to another hard drive or other media, then use GParted to reformat the NTFS partition to EXT.

---

### Post by bodhi.zazen on 2009-12-26
> **NFblaze said:**
> Wait a minute you do realize you ran the e2fsck on **sda2** which is the NTFS partition and not on **sda1** which is the EXT2 partition.

e2fsck is for EXT type partitions formats. Try it again with the correct partitions. If that doesnt work see if you can sudo nano from the terminal and remove errors=remount-ro. 


Also, if you get that working you can backup you stuff on the NTFS partiton by using the LiveCD and copying it to another hard drive or other media, then use GParted to reformat the NTFS partition to EXT.

The OP is trying to fix the "data" partition, which is /dev/sda2 and is formatted as ntfs

The OP is not having problems with the root partition, so e2fsck will not help.

Last, e2fsck can not be run on a mounted partitions, so one would need to run it from a live CD.

---

### Post by NFblaze on 2009-12-26
> **bodhi.zazen said:**
> The OP is trying to fix the "data" partition, which is /dev/sda2 and is formatted as ntfs

The OP is not having problems with the root partition, so e2fsck will not help.

Last, e2fsck can not be run on a mounted partitions, so one would need to run it from a live CD.

I'm sorry I do not see where the OP says data partiton. Could you show me, as I have bad readability in the morning (pills aint kick in yet lol). I do see in his options he has the NTFS to mount read-only by design of his fstab....but I got the gist of him saying that something is mounting read-only and it shouldnt so I thought it was his EXT partitions.

 Anyhow, I've only seen that error message appear for my EXT based partitons, so based on that my bad. Perhaps the OP can clarify.

Also, you do not need to run a LiveCD to run fsck. You can run the fsck program by using the recovery console (which when I've seen this error it usually drops you into), or by entering Single User mode.

---

### Post by bodhi.zazen on 2009-12-26
> **NFblaze said:**
> I'm sorry I do not see where the OP says data partiton. Could you show me, 

Read the very first line of the very first post (emphasis added by me). Subsequent posts will then make more sense to you.

> **keevill said:**
> Suddenly my laptop's **main file storage partition** is read only.

---

### Post by NFblaze on 2009-12-26
> **bodhi.zazen said:**
> Read the very first line of the very first post (emphasis added by me). Subsequent posts will then make more sense to you.

Actually, it's still confusing and a bit ambiguous. Especially, when contrasted with the post title and subsequent other users posts.

Could just be me tho, as I have had problems understanding/translating to normal lingo into computer lingo before. Cool, tho.

---

### Post by keevill on 2009-12-26
> **NFblaze said:**
> Actually, it's still confusing and a bit ambiguous. Especially, when contrasted with the post title and subsequent other users posts.

Could just be me tho, as I have had problems understanding/translating to normal lingo into computer lingo before. Cool, tho.

Sorry for confusing anyone but the replies by bodhi.zazen are correct.
It's the sda2 i.e DATA partition with the problem.
I will go ahead and perform the reformat today after backing up to an alternative media.
-keevill-

---

