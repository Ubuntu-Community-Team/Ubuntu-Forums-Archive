---
title: "need some partition sizing advice"
date: 2009-10-22
forum: General Help
---

### Post by akahige on 2009-10-22
My system has /usr set as its own partition, and sadly that partition is now full. The CD on this system hates for anything to read it, so I can't just fix this with the Live CD, so I'm hoping that there's a way that I can fix this from a running desktop.

I have plenty of space on /home in which to recreate the entirety of /usr (or portions of it, if it's possible to just move some of the subdirectories) -- but I can't quite wrap my head around how to do that.

Can anybody help walk me through this?

---

### Post by alphaniner on 2009-10-22
There's a few possibilities I can think of using symbolic links, but I don't think they could be done on a running system.  Sorry.

---

### Post by kdwillia on 2009-10-22
Do you have the ability to boot your PC from a USB Flash Drive?   You could load a Live CD on a flash drive and do what you need to do.  I have done this on my netbook to change partition sizes.

---

### Post by undecim on 2009-10-22
You can create a bootable thumb drive with System -> Administration -> USB Startup Disk Creator

---

### Post by phillw on 2009-10-22
> **akahige said:**
> My system has /usr set as its own partition, and sadly that partition is now full. The CD on this system hates for anything to read it, so I can't just fix this with the Live CD, so I'm hoping that there's a way that I can fix this from a running desktop.

I have plenty of space on /home in which to recreate the entirety of /usr (or portions of it, if it's possible to just move some of the subdirectories) -- but I can't quite wrap my head around how to do that.

Can anybody help walk me through this?

I'd have a look in /var/logs - This area can grow quite large - especially if something is reporting errors.

These links should help in cleaning your installation ...

[http://ubuntuforums.org/archive/index.php/t-429694.html](http://ubuntuforums.org/archive/index.php/t-429694.html)    - General housekeeping

[http://ubuntuforums.org/archive/index.php/t-87342.html](http://ubuntuforums.org/archive/index.php/t-87342.html)     - That one deals with the /var/logs thing.

Hopefully they will help you get /var back to a reasonable size.

You *could* move and link /var/logs to your home directory - IMO, it'd be better to shrink your /home partition and grow your /var partition.

The above should give you some idea as to where all the room has gone.

The shrinking and growing of partitions is done using a liveCD of GParted 

The site for GParted can be found here (I chose a link for resizing that is roughly what you need)

[http://gparted-forum.surf4.info/viewtopic.php?id=13467](http://gparted-forum.surf4.info/viewtopic.php?id=13467)

DO BACKUP YOUR INSTALLATION BEFORE RESIZING !!!!

[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)

Take your time, don't rush.

Provided you can boot from USB - you can always stick GParted onto a USB stick.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

I *think* I've covered all eventuallities - Feel free to ask if you need any more information.

Regards,

Phill.

---

### Post by SaintDanBert on 2009-10-22
> **akahige said:**
> 
...
The CD on this system hates for anything to read it, so I can't just fix this with the Live CD, so I'm hoping that there's a way that I can fix this from a running desktop.

You can make a live-USB disk or thumb drive with SuperRescueCD or similar.
> **akahige said:**
> 
I have plenty of space on /home in which to recreate the entirety of /usr (or portions of it, if it's possible to just move some of the subdirectories) -- but I can't quite wrap my head around how to do that.

Can anybody help walk me through this?

**Get one or more known good backup copies of all files BEFORE you tinker with file systems.**

Remember that **/home** is a mount point for **/dev/someDisk**.
As far as I know, all users have $HOME as /home/username, so you cannot fix things if logged in as a user. My Ubuntu has a folder /root that gets used as $HOME by a bona fide root login. Notice that this /root folder is not part of the /home tree. This permits root to login even if there are troubles (like, "its full") with the /home device.

Here is one suggestion:
[list=1]
[*]log out of all GUI sessions
[*]use CTRL-ALT-F2 to open a console
[*]login as root [Note -- You will need to have root login enabled for this work. There are several threads that explain how. Ubuntu has this off by default.]
[*]you can now **umount** to separate the /home folder "mount point" from the "/dev/someDisk" file system.
[*]use **mkdir /newName** to create a fresh mount point (see note below)
[*]edit **/etc/fstab** to connect your file system at your fresh mount point.
[*]use **mount /newName** to make your file system contents available.
[/list]

At this point, you will find all of your files at /newName. For example, you will likely see /newName/fred, /newName/wilma, etc for each of your users. (Remember, it used to be /home.) I would likely make a folder /newName/myFolks and **mv** all of the per-user files under there, then create a symbolic link to /newName/myFolks for the name "home" under the root folder "/".
```

user@host# cd /newName
user@host# mkdir ./myFolks
user@host# ls -FC
myFolks/   fred/   wilma/   bambam/   sleepy/   chip/   dale/
user@host# mv -v fred ./myFolks
  'fred' ->  '/newName/myFolks/fred'
... repeat for all users ...
user@host# cd /
... you should already have a mount point folder named "/home"
... you now have /newName/myFolks for your user folders to live
user@host# rm -rf /home
user@host# ln -sf /newName/myFolks /home

```

At this point, you can do whatever you want with the rest of the space at /newName.

**REMINDER: It is always a good idea to make a failsafe backup after you make significant changes to system configuration.**

____________________
Note: When I make a folder that will be used as a file system mount point, I do one extra step as bread crumbs for future troubleshooting.
First make the folder **mkdir /mountPointName**. Next I tag the folder as a mount point using, **touch _THIS_IS_A_MOUNT_POINT_,txt**. When a file system gets mounted, this file is not visible. If it every becomes visible, I know that something is not mounted as planned. Once I have this file, I sometimes edit it to hold notes with other important details.
_____________________

---

### Post by akahige on 2009-10-22
Thanks for all of the advice and links.

I'm going to go through this all very slowly and carefully and see if I can figure out how to fix it.

---

