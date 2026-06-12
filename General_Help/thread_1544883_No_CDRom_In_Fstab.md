---
title: "No CDRom In Fstab"
date: 2010-08-03
forum: General Help
---

### Post by wolvesden on 2010-08-03
Total Newbie here. Been running ubuntu for a solid 24 hours. :p Love it!

I've searched around but really can't find what I'm looking for. I'm hoping someone can point me in the right direction.

My Fstab file does not display my cd/dvd burner drive. Here's what my file looks like.

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

I tried the command "lshal | egrep cdrom" which returned nothing.

I also tried "ls -l /dev/{cd,dvd}*" which returned the following:

ls: cannot access /dev/cd*: No such file or directory
ls: cannot access /dev/dvd*: No such file or directory

I understand how to mount cds and all that good stuff, based on the terrific explainations posted throughout this forum. But i can't mount a cd when i can't find the cd drive.

Any help?

Sorry for the information overload.

---

### Post by dcstar on 2010-08-03
> **wolvesden said:**
> Total Newbie here. Been running ubuntu for a solid 24 hours. :p Love it!

I've searched around but really can't find what I'm looking for. I'm hoping someone can point me in the right direction.

My Fstab file does not display my cd/dvd burner drive. Here's what my file looks like.
........

There is no entry, it is no longer required. CDs and DVDs should mount when inserted **if** the hardware is detected at boot up.

**Exactly** what is the hardware configuration?

---

### Post by Indigo340 on 2010-08-03
Me too, I have no entry for CD-Rom or DVD etc in fstab file and cannot mount the drive or use it at all.
I'm not trying to hijack this thread but I think we have a common problem and will be following to see if it can be resolved.

---

### Post by prshah on 2010-08-03
As already pointed out, since Hardy, dynamic volumes such as CD/DVD drives, USB drives, HDD partitions, etc are no longer required to be listed in /etc/fstab.

If you are facing any problems in your current setup, adding anything to the /etc/fstab will not particularly help.

What problem (if any) are you facing? Usually, CD/DVD devices will be listed as /dev/sr*, as well as /dev/dvd* or /dev/cd*, depending on type; eg```
Tue Aug 03 @14:57:39:~$ ls -l /dev/sr* /dev/dvd*
lrwxrwxrwx  1 root root      3 2010-08-03 10:12 /dev/dvd -> sr0
brw-rw----+ 1 root cdrom 11, 0 2010-08-03 10:12 /dev/sr0
Tue Aug 03 @14:57:48:~$ 
``` (Note /dev/dvd is a symlink pointing to /dev/sr0)

---

### Post by anivegmin on 2010-08-03
Similar problem here.

Although quite often the cd drive and dvd drive will both mount discs immediately after booting the system. But then after some random length of time they will either unmount or wont mount a newly inserted disc.

As I write this post both my drives are inaccessible.

sudo mount /dev/cdrom /media/cdrom

mount: mount point /media/cdrom does not exist

Both drives are listed in Disk Utility -

TSSTcorp CDRW/DVD TSH492B
HL-DT-ST CD-RW GCE-8320B

Both drives work fine with Windows XP.

I have had this problem since installing 10.04 in April. I have posted on various threads on this forum and still not solved it.

---

### Post by wolvesden on 2010-08-03
> **prshah said:**
> 

What problem (if any) are you facing? Usually, CD/DVD devices will be listed as /dev/sr*, as well as /dev/dvd* or /dev/cd*, depending on type; eg```
Tue Aug 03 @14:57:39:~$ ls -l /dev/sr* /dev/dvd*
lrwxrwxrwx  1 root root      3 2010-08-03 10:12 /dev/dvd -> sr0
brw-rw----+ 1 root cdrom 11, 0 2010-08-03 10:12 /dev/sr0
Tue Aug 03 @14:57:48:~$ 
``` (Note /dev/dvd is a symlink pointing to /dev/sr0)


The problem I'm facing, in a nutshell, is CrossOver wants me to mount the StarCraft 2 dvd in a place for it to find it, but I can't put it there cause I can't figure out where the DVD is on the system. 

As far as auto mounting goes, it doesn't seem to be occuring, as I've tried music cds and dvd movies, also with no luck of finding them.

---

### Post by Indigo340 on 2010-08-04
[Quote] What problem (if any) are you facing? [Quote]


I am typing "sudo mount /cdrom0 and getting this response,
 "mount: can't find /cdrom0 in /etc/fstab or /etc/mtab"

If Ubuntu 10.04 does not require entries in these folders in order to mount drives, then why am I getting this response ?

---

### Post by utilitytrack on 2010-08-04
to **Indigo**

try```
# mount /dev/cdrom/ dir
```

or 
```
# mount /dev/dvd dir
```

---

### Post by prshah on 2010-08-04
> **Indigo340 said:**
> sudo mount /cdrom0

It's not "/cdrom", it's "/dev/cdrom".

You can try a manual mount (though it's totally unnecessary) with the command ```
sudo mount /dev/cdrom /mnt -o defaults,ro
```

This will mount the content of your CD at "/mnt".

If this does not work, please check if you have the correct device in /dev; eg /dev/cdrom, /dev/cdrom0, /dev/scd0, etc.

If you still have any problems, please post back errors, if any, as well as the output of the command```
ls /dev/cd* /dev/dvd* /dev/scd* /dev/sr*
```

Once again, I repeat, a manual mount SHOULD not be required.

---

### Post by Indigo340 on 2010-08-04
ian@ian-laptop:~$ mount /dev/cdrom/ dir
mount: only root can do that
ian@ian-laptop:~$ sudo mount /dev/cdrom/ dir
[sudo] password for ian: 
mount: mount point dir does not exist
ian@ian-laptop:~$ mount /dev/cdrom/ dir
mount: only root can do that
ian@ian-laptop:~$ 
ian@ian-laptop:~$ 
ian@ian-laptop:~$ sudo mount /dev/cdrom /mnt -o defaults,ro
mount: you must specify the filesystem type
ian@ian-laptop:~$ ls /dev/cd* /dev/dvd* /dev/scd* /dev/sr*
/dev/cdrom  /dev/cdrw  /dev/dvd  /dev/dvdrw  /dev/scd0  /dev/sr0
ian@ian-laptop:~$

Nothing changed

Sorry I didn't mean to take over this thread, would it be better to start a new thread ?

---

### Post by utilitytrack on 2010-08-04
to **Indigo340**
No, new thread is not neccesary. Please read [FONT=Courier New]man mount[/FONT] carefully.

PS 
"dir" mean "mount point", for example [FONT=Courier New]/media[/FONT] or [FONT=Courier New]/mnt[/FONT].
PPS
filesystem for CDROM is [FONT=Courier New]iso9660[/FONT] generally. Just for experience:
[FONT=Courier New]# mount -t iso9660 /dev/cdrom /media -o defaults[/FONT]

---

### Post by wolvesden on 2010-08-04
I'm starting to think Ubuntu just doesn't see/recognize my cd drive, which seems odd

---

### Post by prshah on 2010-08-05
> **Indigo340 said:**
> 
ian@ian-laptop:~$ sudo mount /dev/cdrom /mnt -o defaults,ro
mount: you must specify the filesystem type
ian@ian-laptop:~$ ls /dev/cd* /dev/dvd* /dev/scd* /dev/sr*

If mount is specifically asking for a filesystem type, then either it has not recognized the CD/DVD in the drive or else there IS no CD/DVD in the drive.

OK, we can go around in circles with this; I think you will be better off with the CDROM entry in the fstab (which is heartily not recommended, not that it can screw your system in anyway).

Add the below line (modify as necessary) to your /etc/fstab```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

Note that any changes to fstab will require a reboot to reflect.

Try this, and please post back to see if it helps in any way; otherwise please post back for better fixes.

---

### Post by Indigo340 on 2010-08-05
To **Utiltytrack, **sorry but that does not mean anything to me, I have been using Ubuntu for about 8 months and don't understand the jargon at all. Plain English please.

To **Prashah, **thanks for the input but I can't edit my fstab file directly, it appears to be locked and I don't know how to access it in Terminal, even if I could access it in Terminal I would not know how to go about adding a line. I have not bothered to learn any of the code for Terminal, I just cut and paste where necessary. Step by step instructions would be most helpful.

I have managed to access the /etc/ file by using cd /etc/ but can't get any further.

---

### Post by Indigo340 on 2010-08-05
OK, I managed to use sudo gedit to add the missing line to the fstab file but after a reboot I inserted a commercially branded (new and working) disc but got this error message, 

Unable to mount MCV 6648 DTSB Iron Man 2

Error mounting: mount exited with exit code 1: helper failed with: mount: mount point/media/cdrom0 does not exist

What did I do wrong ???

Also tried a line from **Utilitytrack, **here is the result,

ian@ian-laptop:~$ mount -t iso9660 /dev/cdrom /media -o defaults
mount: only root can do that
ian@ian-laptop:~$ sudo mount -t iso9660 /dev/cdrom /media -o defaults
[sudo] password for ian: 
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

This means nothing to me, can anyone help me solve this ???

---

### Post by anivegmin on 2010-08-05
Sorry to butt in on this thread again but I have solved my long standing CD/DVD drive mounting problems.

A while back on another thread someone suggested installing the latest kernel (2.6.34). I tried this but no luck.

Well the latest kernel (2.6.35) was released for Ubuntu a couple of days back. This has solved my mounting problems.

Add ppa:kernel-ppa/ppa to your software source list

Reload - then search for "2.6.35" in Synaptic.

Install the following 3 packages (make sure you choose the correct 3 for either 32 or 64 bit. 14 is the latest in the repository so this may change)

linux-headers-2.6.35-14
linux-headers-2.6.35-14-generic
linux-image-2.6.35-14-generic

This kernel will now be the default. Everything now works for me and I have had no problems with it.

---

### Post by utilitytrack on 2010-08-06
> **Indigo340 said:**
> To **Utiltytrack, **sorry but that does not mean anything to me, I have been using Ubuntu for about 8 months and don't understand the jargon at all. Plain English please.

Your answer made an impression to me. I'm speechless.

---

### Post by Nityanandi on 2011-04-25
Happy you took over the thread re no cdrom in fstab. For one application only...installrepo which installs the 9 DVD Ubuntu 10.10 Software Library...it tells me it cannot find /dev/dvd at /media/cdrom because there is no /etc/fstab entry. I'm building that line now. Should have done so before replying to you. Anyhow, Tuxie is glad you posted and took over the thread.

---

### Post by kiran14za on 2012-06-02
Try the below command 

**sudo mount /dev/sr0 /mnt**

Or you can use 

Mount Manager

**sudo apt-get install mountmanager**

---

