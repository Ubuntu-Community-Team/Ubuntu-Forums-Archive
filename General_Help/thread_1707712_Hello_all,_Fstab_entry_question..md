---
title: "Hello all, Fstab entry question."
date: 2011-03-15
forum: General Help
---

### Post by BULLIT22 on 2011-03-15
Hey guys.

Got a few questions about my fstab file. I want to edit it to add 7 hard drives to mount on start up that I share to other pc's and media player devices throughout the house. I'm still new to ubuntu in the sense that I have not done too much rooting around where the average user wouldn't go. I have however taken a fundamentals of Unix class so I think I get MOST of it. 

Anyway, I just want to make sure I have a grasp on things before I enter everything into fstab. I share these drives through smb and don't want to mess anything up with that. OK, on the the specifics of the drive(s).

I have a 1TB drive,  /dev/sdf1. Mounted in, /media/NETWORKTV2. File system is, FAT.

Options, This is what confuses me a bit. I ran the mount command and this is what the options are in there for the drive. 

rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush

Is this what I should use for the Options in fstab?

Then for the dump and fsck I asume would be auto and 0 0.

Thanks for any help in advance.

---

### Post by Krytarik on 2011-03-15
It is generally ok to just take the entries for the concerning partitions out of "/etc/mtab", after they were mounted automatically, if the result is satisfactory. But some of those entries are not 1-to-1 compatible to the expected options for "fstab".

In your case, I believe most of the options could be spared, because they are the defaults.
But I would use the partitions UUIDs instead of their absolute device names.

Please see those guides/manpage, the manpage also states which are the respective defaults for each filesystem:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)
[http://manpages.ubuntu.com/manpages/maverick/en/man8/mount.8.html](http://manpages.ubuntu.com/manpages/maverick/en/man8/mount.8.html)

---

### Post by BULLIT22 on 2011-03-18
Alright, Tried this out on a different PC with an extra NTFS drive in it. I added a line to my fstab file by the UUID like you suggested. When I restarted the system I got a error while mounting drive message and press s to skip or m for manually. Pressed to skip and the drive had mounted anyway.

Although it did not mount in the same way it normally does. It put the drives folders in the mount point instead of mounting the drive in the mount point. 

Anyone have any suggestions as to what I am doing wrong?

---

### Post by Morbius1 on 2011-03-18
Post the output of the following commands so the good folks here can deal with some tangible facts:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
```

---

### Post by BULLIT22 on 2011-03-18
Which machine would you like the output from? The server, or the one I ran a test fstab on? Thanks.

---

### Post by Morbius1 on 2011-03-18
The test PC since it only has one extra partition.

---

### Post by seawolf167 on 2011-03-18
I just want to make sure I'm reading this correctly - you have 7 hard drives in one computer and you want those drives (physically in the computer) mounted automatically upon boot? (versus mounting a networked drive)

As previously said, please post the output of 

```
sudo blkid
gedit /etc/fstab
mount
```

So we can see specifics

---

### Post by BULLIT22 on 2011-03-18
You are correct. I will post the output when I get home from work. Thanks.

> **seawolf167 said:**
> I just want to make sure I'm reading this correctly - you have 7 hard drives in one computer and you want those drives (physically in the computer) mounted automatically upon boot? (versus mounting a networked drive)

As previously said, please post the output of 

```
sudo blkid
gedit /etc/fstab
mount
```So we can see specifics

---

### Post by BULLIT22 on 2011-03-18
sudo blkid -c /dev/null

/dev/sda1: UUID="ec2879ea-af39-40da-a3c1-9199e6295280" TYPE="ext4" 
/dev/sda5: UUID="45671829-2d39-46d8-86b6-9f898551cbfd" TYPE="swap" 
/dev/sdb1: LABEL="Comic Books" UUID="E8E096C2E0969702" TYPE="ntfs" 

_____________________________________________________________________________________

gedit  /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ec2879ea-af39-40da-a3c1-9199e6295280 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=45671829-2d39-46d8-86b6-9f898551cbfd none            swap    sw              0       0

/dev/sdb1 /media/ ntfs rw,nosuid,nodev,allow_other,blksize=4096,default_permissions auto 0 0


_____________________________________________________________________________________


mount

/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media type fuseblk (rw,nosuid,nodev,allow_other,allow_other,default_permissions,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/deadpool/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=deadpool)


_____________________________________________________________________________________


Thanks and let me know what you all think. I edited the fstab with the UUID and the Label.

---

### Post by Krytarik on 2011-03-18
You didn't specify a mount directory in "/media". You may need to create one before.

I would put the mount options in "fstab" rather like this:```

UUID="E8E096C2E0969702" /media/Comic\ Books ntfs-3g rw,nosuid,nodev,allow_other,default_permissions,umask=000,utf8=1 0 0
```"umask" is set here to "allow everything to all", maybe that is needed in your case to allow your external clients access.
Also see: [http://en.wikipedia.org/wiki/Umask](http://en.wikipedia.org/wiki/Umask)

---

### Post by BULLIT22 on 2011-03-18
ok, I tried it the way you have it with the comic\ books one time around and still had the same error. The directories in the drive are mounted in Media/ either way. I'll give it a go again and let you know.

---

### Post by BULLIT22 on 2011-03-18
Alright, Just changed it and did a restart. Same error on start-up. 

The Directories did not mount into /media/ this time but instead created a Comic\ directory. with nothing in it. Here's the fstab file after I changed it to what you had stated.

 # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ec2879ea-af39-40da-a3c1-9199e6295280 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=45671829-2d39-46d8-86b6-9f898551cbfd none            swap    sw              0       0

UUID="E8E096C2E0969702" /media/Comic\ Books ntfs-3g rw,nosuid,nodev,allow_other,default_permissions,umask=000,utf8=1 0 0

---

### Post by Krytarik on 2011-03-18
Ah, I hate those space issues (it's the same in Windows). ;-)

In fact, I don't use spaces in the mount points, it was just an assumption that it should work that way, I saw it in another forums thread recently.

You may either use a "-" instead or try it that way:
```
/media/"Comic Books"
```**EDIT:** That way may also work (should have googled it before):
```
/media/Comic\040Books
```

---

### Post by BULLIT22 on 2011-03-19
Alright bud. I think we got this one solved. Thank you very much. The /media/Comic\040Books was the only one that did it. If I wouldn't have put a space in there when creating the drive we wouldn't have been here. Thanks you so much for your help.

---

### Post by Krytarik on 2011-03-19
> **BULLIT22 said:**
> If I wouldn't have put a space in there when creating the drive we wouldn't have been here. Thanks you so much for your help.
At least you got also the correct options by that way.

You're welcome!

---

### Post by BULLIT22 on 2011-03-19
Yes the option are working as well too. Almost forgot that. Thanks.

> **Krytarik said:**
> At least you got also the correct options by that way.

You're welcome!

---

### Post by BULLIT22 on 2011-03-19
Well, I'm trying to do the drives in my main PC now and have edited the fstab file. It mounts but I am getting the startup error again. Could this be due to the permissions? this is what the line looks like that I have added.

UUID="D652-84DE" /media/movies vfat rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec 0 0


Thanks for the help again!

---

### Post by BULLIT22 on 2011-03-19
Nevermind. I changed the dmask= to umask=000 and no error.

---

### Post by Colin Keenan on 2011-03-22
Even though your question is solved, I don't think anyone explained the uhelper=udisks option.  I was searching on that when found this.  I knew that whenever I mounted something from the "Places" dropdown menu, it put the "uhelper=udisks" option in /etc/mtab (which is a file that lists everything mounted).  And, like you, I wondered if I needed that option in etc/fstab if I wanted to automatically mount on boot-up.

Turns out, the easiest way to get the mount to behave exactly as if you chose the disk from the "Places" menu is to use the following command:

udisks --mount /dev/[fill in the device]

So for your /dev/sdf1 disk, you would mount it with:

udisks --mount /dev/sdf1

And, do NOT use "sudo".

To automatically mount whenever you login, just add that to your Startup Applications.  For example, goto System -> Preferences -> Startup Applications [+Add] 
Name: Mount NETWORKTV2
Command: udisks --mount /dev/sdf1

Easiest way and no messing around with options you don't really understand in the fstab file.

---

### Post by Morbius1 on 2011-03-22
Well, since everyone else if publishing their favorite method I though I'd share mine. I prefer the "template" approach. What most users apparently don't know is that you can have the installer create an entry in fstab for all these non-system partitions so that when you boot for the first time all of them will mount at boot. You tell the installer where you want it to mount and how its formatted and it does the rest.

What the Ubuntu installer will do is create fstab entries based on these templates depending on how the partition is formatted:
> UUID=DA9056C19056A3B3 /windows/WinXP2 **[COLOR=Blue]ntfs[/COLOR]**   defaults,nls=utf8,umask=007,gid=46 0       0
UUID=C4DB-C1B0  /windows/J      **[COLOR=Blue]vfat[/COLOR]**    utf8,umask=007,gid=46 0       1
UUID=e92eaf02-ff61-4db0-9397-35f1aadb98e8 /VMLIN **[COLOR=Blue]ext4[/COLOR]** defaults        0       2You can use these templates to create your own entries simply by running "sudo blkid -c /dev/null" to find the correct UUID number and then creating your own mount points.

You can delve into what each parameter means or you can use blind faith that Ubuntu knows what it's doing. I personally modify them a bit for my own reasons but that's not required.

I for one prefer the more traditional method of having mounts in fstab with recognizable and coherent options as the one's used in the templates. It seems to have worked for UNIX / Linux for decades now. :wink:

---

