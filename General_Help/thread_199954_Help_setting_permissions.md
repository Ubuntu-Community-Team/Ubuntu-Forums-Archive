---
title: "Help setting permissions"
date: 2006-06-19
forum: General Help
---

### Post by Roman27 on 2006-06-19
What command can I use to change the permissions of only the directories in an entire tree (recursively)?

---

### Post by Ramses de Norre on 2006-06-19
I've got to this, but I haven't used this much before and I get errors on output, I don't understand why.. maybe it does work like this already and it just ignores the errors but I hope someone can make it better (and learn me how to do it better too ;))
 ```
#!/bin/bash
for i in /path/* 
	do if [ -d $i ]
		then chmod -644 $i
	fi
done

```

---

### Post by mannheim on 2006-06-19
The [Wikipedia entry for chmod]("http://en.wikipedia.org/wiki/Chmod") tells you how to do this, using "find". See the last of the "Examples" in the wikipedia entry.

---

### Post by aysiu on 2006-06-19
What you're requesting can be a very dangerous operation. Can I ask why you want to change the permissions?

If you modify the permissions of certain folders or files (yes, even in your home folder), you can render your system virtually unusable.

---

### Post by Roman27 on 2006-06-19
[QUOTE=aysiu]What you're requesting can be a very dangerous operation. Can I ask why you want to change the permissions?

If you modify the permissions of certain folders or files (yes, even in your home folder), you can render your system virtually unusable.[/QUOTE]
The reason is that I recently replaced an old dedicated 160GB FAT32 drive with a 250GB XFS drive by copying the files from the old to the new drive in Nautilas while booted to the Live Dapper CD.  Now the perms are a little messed up on it.   I use another drive to install Linux/Windows on.

Anyway, I've managed to chown everything to root.  But, the perms are giving me trouble.  I don't feel secure making everything chmod 777, but I have to have some flexibility in the perms because I'm using Samba to share this drive for my wife to access via Windows XP.

I'm kinda lost on setting a permission strategy.  It looks like everything I create in Ubuntu (on the machine housing the drive) is under my account with perms that don't allow my wife to modify it.  Anyway, I need some help, but for starters it would be nice to be able to open directories.

---

### Post by aysiu on 2006-06-19
Thanks for the explanation. I just wanted to make sure we're not enabling your doom. Sounds good.

Generally, to recursively set permissions, you'd do something like ```
sudo chmod -R 775 /nameofdirectory
``` The *-R* flag makes the permission change work recursively.

For your other problem regarding permission strategy, [this](http://www.ubuntuforums.org/showpost.php?p=832721&postcount=9) may help.

---

### Post by Najand on 2006-06-19
Hmm, why don't you add your wife's User ID to the group with the same name as your user ID. Your wife then can access to all directories you have made or you have access to, easily.

---

### Post by aysiu on 2006-06-19
[QUOTE=Najand]Hmm, why don't you add your wife's User ID to the group with the same name as your user ID. Your wife then can access to all directories you have made or you have access to, easily.[/QUOTE]
That doesn't work, believe it or not. Read the thread I linked to above.

---

### Post by tonyr on 2006-06-19
[QUOTE=aysiu]Thanks for the explanation. I just wanted to make sure we're not enabling your doom. Sounds good.

Generally, to recursively set permissions, you'd do something like ```
sudo chmod -R 775 /nameofdirectory
``` The *-R* flag makes the permission change work recursively.

For your other problem regarding permission strategy, [this](http://www.ubuntuforums.org/showpost.php?p=832721&postcount=9) may help.[/QUOTE]

I'm flagging this as possibly misleading.  The original request was to change the 
permissions on **only the directories**.  **chmod -R** changes the permissions
on **all files**.  The suggestion by **mannheim** about using **find** allows a more
selective application of **chmod**.

EDIT: I haven't looked at the wiki that **mannheim** indicated, but I would expect it
to say something like:

[COLOR="Sienna"]As root, cd to the topmost directory to be affected, then do[/COLOR]
[COLOR="Blue"]find  .   -type  d  -exec chmod 775 {} \;[/COLOR]

Arcane syntax, to be sure, but it works.

---

### Post by Najand on 2006-06-19
Thanks, aysiu and sorry for my poor knowledge. For my information, is there any solution like making his wife a sudoer and then let her sudo to access his account?

---

### Post by aysiu on 2006-06-19
[QUOTE=tonyr]I'm flagging this as possibly misleading.  The original request was to change the 
permissions on **only the directories**.  **chmod -R** changes the permissions
on **all files**.  The suggestion by **mannheim** about using **find** allows a more
selective application of **chmod**.[/QUOTE]
Oops. I guess I didn't read the original post carefully.

Can I ask what the point of having permission to a directory if you don't have permission to the files within that directory...? There's probably some practical use for that, but I just can't think of it right now.

---

### Post by tonyr on 2006-06-19
[QUOTE=aysiu]
Can I ask what the point of having permission to a directory if you don't have permission to the files within that directory...? There's probably some practical use for that, but I just can't think of it right now.[/QUOTE]

I agree.  Something for **Roman27** to take into consideration.

---

### Post by Najand on 2006-06-19
what about using  find command?
```
find . -type d -exec chmod 777 '{}' \;
```

---

### Post by Roman27 on 2006-06-20
Thanks everyone for the help.  I solved the issue with the **find** command detailed in the [Wikipedia]("http://en.wikipedia.org/wiki/Chmod") and mentioned by tonyr and mannheim.  It worked flawlessly.

---

### Post by Graybeard on 2006-06-20
I have a similar task. I periodically clone my internal HDD to an identical rack-mount HDD to backup all of my tweaks to the OSs (both XP and Ubuntu) and Apps as well as my data.

Having just recently installed Dapper, I can't access the rack-mount drive to copy data to the internal drive. I don't have permission! Can I "sudo chmod -R 775 /nameofdirectory" to make it accessible?  And if so, will "/hdd" be sufficient address?

---

### Post by tonyr on 2006-06-20
This doesn't sound like the same kind of problem.  Does your system see the 
other (clone target) drive at all?  When you say 'rack mount', do you mean
**external**, and if so, how is it connected?  If not **external**, then what?

If you are comfortable using a terminal, do
```

sudo fdisk -l

```
(that's an ELL, not an EYE)

and post the output here.  Otherwise, run **gparted** 
(System->Administration->Gnome Partition Editor), see what it says about
devices and partitions, and report that here.

---

### Post by Graybeard on 2006-06-20
fdisk -l shows
Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        6527    52428096    7  HPFS/NTFS
/dev/hda2            6528       19581   104856255    c  W95 FAT32 (LBA)
/dev/hda3   *       19582       24124    36491647+  83  Linux
/dev/hda4           24125       24321     1582402+   5  Extended
/dev/hda5           24125       24321     1582371   82  Linux swap / Solaris

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        6527    52428096    7  HPFS/NTFS
/dev/hdd2            6528       19581   104856255    c  W95 FAT32 (LBA)
/dev/hdd3           19582       24321    38074050    f  W95 Ext'd (LBA)
/dev/hdd5           19582       19645      514048+  82  Linux swap / Solaris
/dev/hdd6           19646       22026    19125351   83  Linux

hdd is the backup disk. It's in a Kingwin-KF101 rack mounted in a 5-1/4" bay and connects on insertion to the same ribbon cable that the CDRW drive connects to, whatever that's called. This is the same arrangement used in the computer I'm replacing which was a Dell 4550.

I hope that helps. If you need other information, I'll do my not-very-competent best.

BTW, It shows up in "System -> Administration -> 
Disks" but is listed as "inaccessible" and if I click "enable" I get no response. I recall getting a "permission denied" or something of that sort on an earlier attempt but don't recall what I was doing when I got that response. 

Bob

---

### Post by tonyr on 2006-06-20
OK.  This looks promising.  the system sees the second drive.  Now in a terminal do
```

mount
cat /etc/fstab

```

The **mount** command shows which devices are mounted, and **cat /etc/fstab**
shows what the mounting plan is when your  machine boots.  You also need to verify
that the CDRW and the second drive are not conflicting with each other.  You can usually 
figure this out by going inot the CMOS Setup screen early on in the boot sequence
(somewhere it will say something like 'Press Esc for Setup', or maybe Del or one
of the F keys.  I am assuming that the drives and CDRW are IDE devices, not SATA.
Can you confirm that?  

Maybe during the boot sequence there is some information displayed that shows
what devices are master and which are slaves.   That information should also be
in the CMOS Setup somewhere, maybe on the first page or under Peripherals.

---

### Post by tonyr on 2006-06-20
...and a couple more questions...
Was the second drive already partitioned and formatted, or did you partition and
format it yourself?  Was it being used in the old replaced computer the same way?

Here is something else to try if the previous **mount** command showed that
the **hdd**n partitions were not already mounted.  In a terminal do

```

cd /media
ls -l

```

If there are no directories with names that start with **hdd**, make some:
```

sudo mkdir hdd1 hdd2 hdd6

```

and try to mount the partitions manually:
```

sudo mount -t ntfs /dev/hdd1 /media/hdd1
sudo mount -t vfat /dev/hdd1 /media/hdd2
sudo mount  /dev/hdd6 /media/hdd6

```

If that last one doesn't work, try adding **-t ext2** or **-t ext3** between
the **mount** and the **/dev/hdd6**.

---

### Post by Graybeard on 2006-06-20
OK, here are the results of "mount" and "cat /etc/fstab:

/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-23-386/volatile type tmpfs (rw)
/dev/hda2 on /FAT32 type vfat (rw,iocharset=utf8,umask=000)
/dev/hda1 on /tmp/disks-conf-hda1 type ntfs (rw)
/dev/hdd1 on /tmp/disks-conf-hdd1 type ntfs (rw)

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda2       /FAT32          vfat    iocharset=utf8,umask=000 0 0

I hope it makes sense to you because it's all 30,000 feet over my head. And yes, all are IDE.

Bob

---

### Post by Graybeard on 2006-06-20
Sorry, you added questions while I was composing a reply and I didn't notice until now.

The drive now used in the rack for backup was new and unformatted. I cloned the internal drive to it using g4u before removing Xandros and installing Ubuntu. I then checked that it was readable, and found that it was. And, indeed, Ubuntu "sees" it and identifies the partitions on it but won't let me access it. As a true clone I should be able to switch the drive itself (inside the cassette) with the internal drive, power up, and get the Lilo menu choices of XP or Xandros. My immediate goal is to extract my extensive business-related email archives and FireFox bookmarks, import them, and when I'm sure there's nothing else of consequence on that drive and only that drive, then clone the current internal to the rack-mount drive. There are work-arounds to get the data but sooner or later I need to be able to mount and access the drive.

Bob

---

### Post by tonyr on 2006-06-20
OK, sorry about the technical stuff.  The **mount** and **fstab** results confuse
me a little because there is no mention of either **hda1** or **hdd1** in the
**fstab** file.

I still need to know a little background.  How were you doing the 'cloning' before? Was it
a simple copy, or were you using an application?  Were you doing it all from Windows
previously and now you want to reproduce the process in Ubuntu?

The bottom line here is that Windows NTFS type partition handling (NTFS is
the partition type used by XP) is relatively young in Linux, and still classified as
**experimental**, I believe.  Ubuntu has chosen to make it hard for a novice user 
to do much of anything but read from an NTFS partition, and it takes a little extra
work even to make that happen.  Read [this]("https://help.ubuntu.com/community/NTFSReadWrite") article.  

If I am guessing right, and you have been doing this cloning in the past from
Windows,  I would suggest that you continue to do that for the Windows filesystems.
Windows will not recognize Linux partitions, and so they will not show up under
**My Computer** at all.  The article I mentioned above says that there is a Linux
utility, **nfsclone**, that can be used to backup NTFS partitions, but I would
suggest great care in using it at this stage.  You should be able to copy the Linux
partition without much problem, but you should do it as the user **root** with the
**sudo** or **gksudo** commands in a terminal.

---

### Post by Graybeard on 2006-06-20
No, the cloning has not been done from Windows. For a couple of years now, since I first started using Linux in the Xandros distro, I've been using g4u which is similar in function to Norton Ghost. It's a Linux live-CD running a program developed primarily for enterprises needing to put identical OSs and Apps on multiple desktops. It has several functions and the only one I use is "copydisk" which copies a hard drive, bit for bit, onto another. Working bit for bit it is OS independent and obviously makes a copy of every tweak to every app in addition to user data that is customarily backed up. And includes the MBR. And includes the formatting of the disk being cloned. And takes just as long to clone a disk that is 90% empty as it does to clone one that is 90% full.
In a word, it's not a copy; it's a true clone. If you're unfamiliar with this kind of thingamabbob, go to [www.feyrer.de/g4u/](www.feyrer.de/g4u/) 

Bob

---

### Post by tonyr on 2006-06-20
Thanks, I was just looking for a frame of reference.  

Does **g4u** not work for you now, or was that the genesis of your
original post?

The native tool in UNIX/Linux for cloning a hard drive is **dd**.  There may be a UI 
for it around somewhere, but I've just always used it from the command line.  It does a
raw copy between devices, as you described.  You are fortunate in that your main
drive and your backup drive are identical.  You could do a partition by partition copy,
or you could simply copy the whole disk at once.  The advantage to copying the
whole disk at once is that the partition structure of the main drive would be reproduced
exactly on the backup drive.  Otherwise, for safest results, you would need to 
manually insure that the partition structures of the two drives are the same 
(which, I must tell you, they are not currently).

In your case the command to clone the whole drive is, in a terminal
```

sudo dd if=/dev/hda of=/dev/hdd bs=512

```

where **if** specifies the drive to copy **from** (**i**nput **f**ile),
**of** specifies the drive to copy **to** (**o**utput **f**ile), and
**bs=512** is the basic blocksize (in bytes) of the drives.  Needless to say,
don't get the **if** and **of** confused.

There is plenty of information about **dd** and it's use out there in webland.
I did a search on **dd** and **howto**.

---

### Post by Graybeard on 2006-06-20
I had looked into DD but with my inexperience with the command line I decided that g4u, which has both whole-disk and a partition clone commands in its current version. But we stray from the current concern: How can I access the rack-mounted disk if Ubuntu sees it but won't let me access it? Is it, after all, a permissions problem?

Bob

---

### Post by tonyr on 2006-06-20
After all that, I think it is, but it is not straightforward to fix, and **chmod -R** will,
unfortunately, not do the job.  In a terminal do
```

sudo umount /tmp/disks-conf-hdd1
sudo mount -t ntfs -o defaults,umask=0  /dev/hdd1 /tmp/disks-conf-hdd1
sudo umount /tmp/disks-conf-hda1
sudo mount -t ntfs -o defaults,umask=0  /dev/hda1 /tmp/disks-conf-hda1

```

I am assuming that **/tmp/disks-conf-hdd1** and **/tmp/disks-conf-hda1**
still exist after the **umount** commands.  If they do not, you will have
to create some appropriate directories, usually **/media/hda1** and **/media/hdd1**,
and use those instead, thusly 
```

sudo mount -t ntfs -o defaults,umask=0  /dev/hdd1 /media/hdd1
sudo mount -t ntfs -o defaults,umask=0  /dev/hda1 /media/hda1

```

That sequence of commands would have to be repeated after each reboot.  To fix
it permanently, you would need to add a couple of lines to the file **/etc/fstab**,
which you can only edit as root.

Your existing /etc/fstab looks like this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda3 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hda2 /FAT32 vfat iocharset=utf8,umask=000 0 0

```

The modified one should look like this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda3 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hda2 /FAT32 vfat iocharset=utf8,umask=000 0 0
/dev/hda1 /media/hda1 ntfs defaults,umask=0 0 0 
/dev/hda1 /media/hdd1 ntfs defaults,umask=0 0 0 

```

(Note that I used the **/media/hdxx** names; use the other, original, ones
if you prefer.)

Then reboot.  This should give you read access to everything on the main drive
XP partition and the backup XP partition.

---

### Post by Graybeard on 2006-06-20
Hmmmmmm.    This seems to be well beyond my self-confidence level. I hate to do things if I don't understand what I'm doing. I'm happy to cut and paste to save possible errors but only when I understand what I'm cutting and pasting. This is not a question of trust, understand, it's a matter of the way I'm put together. 

Since 99% of the data I want to migrate is also on a 60 gB drive from the old Dell, I think maybe I'll try installing that as a second internal drive in the new box and see if I can then copy the essentials onto the 200 gB master drive. If that works and I'm happy I've got everything I really need, I'll then make a new clone of the internal to the rack-mount. At least if I screw up by dropping a screwdriver I'll have only myself to blame. 

Being able to access the clone for purposes other than salvaging after a disaster will just have to await growth in confidence.

I'll post a summary of how things worked, or didn't.

Bob

---

### Post by tonyr on 2006-06-20
I understand.  This Ubuntu policy of making NTFS partitions 'hard to get to' is unfortunate,
and has frustrated many people.  Good Luck.

---

