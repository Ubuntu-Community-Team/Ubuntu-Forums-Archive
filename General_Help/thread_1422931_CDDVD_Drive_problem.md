---
title: "CD/DVD Drive problem"
date: 2010-03-06
forum: General Help
---

### Post by Snowball10 on 2010-03-06
I'm trying to install a few windows applications into WINE, but the disc drive isnt recognizing anything in there. under the computer section in file browser, it detects that the drive is present, and I can view properties and what not, but absolutely no information on the contents of the disc in the drive is available.

 Under the properties of the disc drive, it lists the volume, accessed and modified information as "unknown" and it also says that "the permissions of "CD/DVD Drive" could not be determined"

Soemtimes, it will detect information about the disc immediately after restarting, but it disappears again when I try to do anything with it. I've also tried using different discs, blank, and even the OS disc I installed Ubuntu from, all detecting nothing.

Thanks for your help,

---

### Post by flippo on 2010-03-06
Are you sure the drive works (have you tested it on a windows install or something similar)?

Can you provide the contents of your /etc/fstab and print the output of ```
sudo ls -l /media
```

---

### Post by Snowball10 on 2010-03-06
I'm afraid I haven't the foggiest idea what an etc/fstab is, i'm still new at this, but the code you asked for is as follows:```
jeff@computer:~$ sudo ls -l /media
[sudo] password for jeff: 
total 8
lrwxrwxrwx 1 root root    6 2010-03-03 09:12 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2010-03-03 09:12 cdrom0
drwxr-xr-x 2 root root 4096 2010-03-03 09:12 cdrom1
jeff@computer:~$ 

```

Also, yes the drive did work on windows XP before switching to Ubuntu.

---

### Post by flippo on 2010-03-06
For the fstab type into a terminal```
sudo cat /etc/fstab
```

I see two cdrom devices in your /media, do you have a second drive?

---

### Post by Snowball10 on 2010-03-06
```
jeff@computer:~$ sudo cat /etc/fstab
[sudo] password for jeff: 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=0cba75f1-0f05-4e51-9bca-8dbde168981b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0fdcc4bd-921a-4807-a87f-299171c12e4d none            swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
jeff@computer:~$ 

```

I think the other drive you're seeing is my memory card reader, but I could be wrong, however there is no other CD drive on this computer I'm aware of, but it would be a pretty impressive trick to keep it hidden.

---

### Post by flippo on 2010-03-06
Have you used the memory card reader?
Did it work?
Has your CDROM drive ever worked on this installation?
Try changing the line:```
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```in your /etc/fstab to```
/dev/scd0       /media/cdrom1   udf,iso9660 users,exec,utf8 0       0
```Then restart and insert a cd, tell me what happens

be sure to back up your fstab first though:```
sudo cp /etc/fstab /etc/fstab.bup
```

**To change /etc/fstab type```
gksudo gedit /etc/fstab
```in a terminal

---

### Post by Snowball10 on 2010-03-06
No luck, I'm thinking that I should switch out this drive (a CD RW/DVD RW) with the CD RW/DVD it originally came with. I can't imagine that would have much of an effect, it came from the same model computer, but it can't hurt to try?

This drive worked fine when i first tried ubuntu, I was dual booting ubuntu and XP, but after I started having problems with the internet and this drive, I  switched to full Ubuntu, fixing the internet problems, but clearly not the ones with this drive.

The memory card reader works perfectly, I tested it again a moment ago.

---

### Post by flippo on 2010-03-06
What is the output of:```
ls /dev/ | grep scd
```
Also:```
ls -l /dev/ | grep cdrom
```

Please change your fstab back to the original.

---

### Post by Snowball10 on 2010-03-06
I turned it on this mornining, and inexplicably it's working, so I guess changing the fstab did work, but i'm not sure why it took this long.

Thanks for all your help, I can't tell you how much i appreciate it.

---

