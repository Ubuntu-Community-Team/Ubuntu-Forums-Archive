---
title: "HOWTO: Mount Windows (NTFS) drives"
date: 2004-10-24
forum: General Help
---

### Post by adeh on 2004-10-24
Hi, 

I've just installed Ubuntu and while I am not a pure noob, I am having trouble with one thing. I can successfully mount my ntfs partition using 
sudo mount -t ntfs /win/d /dev/hda8 
This works fine and while I am in the root terminal, I can cd around and see my files. However, it mounts as a read-only file system (I know this is because ntfs is read only in linux at this point), but it also loads with permissions set to 500, meaning that when I browse to the directory in Nautilus using my normal user, I can't see anything. I have tried
sudo chmod 555 -r /win
but that does not change anything.

Basically, I want to read the music and jpeg files I have on that drive as a non-root user. Any ideas?

Thanks in advance,
Adeh

---

### Post by beesee on 2004-10-24
Here's how I mount my ntfs partition:  In /etc/fstab is have this line:
```
/dev/hda1  /mnt/win  ntfs  nls=iso8859-1,ro,umask=0  0  0
```
This will mount the partition on boot.  You'll also be able to mount it manually by just issuing a
```
# sudo mount /mnt/win
```
You can check the fstab and mount man pages for more info.

Also, this probably isn't the section where questions should go.  It's really just a place for people to post tips and tricks and things like that.

---

### Post by adeh on 2004-10-24
Thanks for your help beesee, but I actually already have the mounting part taken care of. I was hoping someone might have experienced the same problem I had where nothing is viewable. 

I noticed that there was no HOWTO for this and so I thought that this thread might serve as one once we got enough answers.

Thanks again,
Adeh

---

### Post by oddabe19 on 2004-10-24
[QUOTE=adeh]Hi, 

I've just installed Ubuntu and while I am not a pure noob, I am having trouble with one thing. I can successfully mount my ntfs partition using 
sudo mount -t ntfs /win/d /dev/hda8 
This works fine and while I am in the root terminal, I can cd around and see my files. However, it mounts as a read-only file system (I know this is because ntfs is read only in linux at this point), but it also loads with permissions set to 500, meaning that when I browse to the directory in Nautilus using my normal user, I can't see anything. I have tried
sudo chmod 555 -r /win
but that does not change anything.

Basically, I want to read the music and jpeg files I have on that drive as a non-root user. Any ideas?

Thanks in advance,
Adeh[/QUOTE]

here's how I have mine in FSTAB
```
/dev/hda1   /media/winxp  ntfs  users,umask=0222,ro  0  0
```  I'm pretty sure that's how it is, i can't remember off the top of my head, i'm on my 'rents computer right now.

---

### Post by beesee on 2004-10-24
Have you tried using my (or oddabe19's) fstab line?  The umask option is the part that controls permissions.  So if you're having access problems then umask might the answer.

---

### Post by chz on 2004-10-25
i had the problem you had...where it showed the directories as files instead of folders...and you could only access them as root and not as user...well..this is what fixed the problem

dev/hdc1	/disks/Win	ntfs	ro,uid=1000,auto	0	0

i read somewhere it had to do with the user issues...i dont know the exact details...but this works for me...and it does it on boot too...

uid is set to my user id...im the only one that accesses the drive...and the only one that uses the computer...so it didnt matter making global...

---

### Post by mhael on 2004-10-25
Ubuntu kernels include new 2.x version of NTFS driver with more precise control over file/directory permissions. New mount options -  'dmask' and 'fmask' allow to set different umask values for directories and files.
So now we can hide that annoying execute bit from files on NTFS partitions  ;) 

Here my fstab entry:
```
/dev/hda1       /mnt/ntfs-sys   ntfs     ro,dmask=0222,fmask=0333   0 0
```

---

### Post by adeh on 2004-10-25
Great, the fstab trick rocks. So much for trying to go one step at a time :). Thanks everyone for your help... and I do believe we now have a solid HOWTO mount win partitions in Ubuntu.

Thanks,
Adeh

---

### Post by teknoweeeny on 2004-10-27
Ok guys and gals...
I have tried all the above and many more variations of these in one form or another. what the heck am i doing wrong. I will deffinately admit to being a n00b, but this is rediculous here is the last version of my mount line in /etc/fstab-
/dev/hda1	/mnt/Windows	ntfs 	nls=iso8859-1,ro,umask=0  0  0
it is using the last format posted on this thread. I have used all of the ohers as well.
I need Help.

---

### Post by princemackenzie on 2004-10-27
/dev/hda1 /windows/C ntfs ro,uid=1000,auto 0 0

Is what I use.  Make sure that the directory (in this case /windows/C) actually exists.  Otherwise get to a terminal and create it. 

sudo mkdir /windows
sudo mkdir /windows/C

In the boot up dialog, you can see when it gets to the "mounting filesystems" line what happens, and if any errors come up.

Tell us what happens.

---

### Post by jivens on 2004-10-28
Actually several of the different fstab entrys noted work for me; my question: is there a way to make my WinXP drive hda1 (primary master, Ubuntu is on primary slave hdb1) show up in the menu along with filesystem,cdrom, etc. under computer-disks and/or on the desktop.

Thanks in advance, Jeff

---

### Post by kamstrup on 2004-11-02
If you mount drives under /media/my_drive it will show up on the desktop and in "Computer" as "my_drive".

---

### Post by kamstrup on 2004-11-02
I had problems myself getting a fat32 partition to be readable to users. Adding the following line to /etc/fstab fixed that:

/dev/hda1       /media/windows  vfat    umask=0,user,codepage=850,exec  0 0

---

### Post by ward on 2004-11-03
I'm a noob and the only problem I have, so far, is editing my fstab. I get the error "Cannot edit /etc/fstab." How can I edit that file or any "no edit" file?

---

### Post by kensai on 2004-11-03
[QUOTE=ward]I'm a noob and the only problem I have, so far, is editing my fstab. I get the error "Cannot edit /etc/fstab." How can I edit that file or any "no edit" file?[/QUOTE]
 Did you tried?:
#sudo nano /etc/fstab

---

### Post by ward on 2004-11-03
Ok, yeah didn't even know that command existed. Thanks!

---

### Post by tanari on 2004-11-05
I can't delete files from fat32 partition! even if I login as root!!

This is my fstab line:
```

/dev/hda5	  /mnt    vfat   users,umask=0,ro,uid=1000,auto 0  0

```
how to set permissions for /mnt to 755 or 777?

---

### Post by tanari on 2004-11-05
I have solved my problem, now I can delete, rename, and see files in user mode, 

/dev/hda5	  /mnt    vfat  users,uid=1000,auto 0  0

---

### Post by eremite on 2004-11-30
It looks like all the questions here have been for mounting the windows partition of a single hard drive where linux is on another partition (I take it hda1, for example, is partition 1 of the master hard drive hda?).

My system has two hard drives: master has winxp, slave has ubuntu. When I'm running ubuntu, I can't see any of the files on the other hard drive with windows on it (I have gigs and gigs of music and other files I'd like to access). 

My question is: can I use one of the commands above in previous posts, only specify hda? Would that work? Thanks for assisting a beginner.

---

### Post by adbak on 2004-11-30
[QUOTE=eremite]My question is: can I use one of the commands above in previous posts, only specify hda? Would that work? Thanks for assisting a beginner.[/QUOTE]
Assuming that there's only one partition (or that Windows is the first partition) on your primary harddrive, the master one, then you would have to specify "/dev/hda0".

The "a" in the "hda0" means that it's the first drive and the "0", using Unix's method of counting (which starts at zero), means that it's the first partition.  Therefore, hdb3 would signify the second drive's third partition.

[EDIT] Since there's no reliable way for Linux to write to NTFS now, make sure that you make it read only.  I don't know how to do that, but I'm sure if you Google it ([http://www.google.com/linux](http://www.google.com/linux)) you'll find a way.

---

### Post by pavkonti on 2004-12-05
how to mount an exteded partion?

```

/dev/hda1       /media/windows ntfs ro,uid=1000,auto 0 0
/dev/hda2       /media/storage    
/dev/hda4       /               reiserfs defaults        0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

hda1 works fine, but what to type for my second partion?

---

### Post by mhael on 2004-12-06
[QUOTE=pavkonti]how to mount an exteded partion?
[/QUOTE]

Use /dev/hda5 for first logical drive in extended partition, /dev/hda6 for second logical drive in extended partition and so on...

---

### Post by piedamaro on 2004-12-28
What about removable ntfs usb drives? Why hotplug/d-bus/hal/g-v-m can't automount them?
Adding a static line in fstab is not an option, cause if you have more than 1 removable drive, it screws up automounting.
It recognize the drive, then it parses all kind of filesystem, try to mount it as xfs or something and then fails.
This is the major issue I'm having with ubuntu, any hellp is really appreciated :)

---

### Post by Spence2 on 2007-05-28
Thanks,
This is what worked for me:
```

su root
cd /media
mkdir windows
nano /etc/fstab
type or paste the line: /dev/hda1 /media/windows ntfs ro,dmask=0222,fmask=0333 0 0
mount /dev/hda1
then cd /media/windows
ls (all your windows files+folders will be listed)

```
It was hda1 for me, since the linux partition was hda2 (as listed in /etc/fstab) but it can be hdc, hdc1, hda, etc so you'll have to check what the other partitions are labeled as.

Greetings, 
Spence

---

