---
title: "USB devices auto-mount as read-only...sort of"
date: 2010-09-19
forum: General Help
---

### Post by snowveil on 2010-09-19
My 10.04 64-bit desktop has been auto-mounting USB devices (flash drives and my mp3 player) as read-only for some reason.  I had this issue happen once a while in the past, so I simply re-mounted it as rw.

However, even manually mounting these devices as rw does not solve the problem.  I ran a few commands ahead of time to give you an idea of what we're looking at: 

```

mike@mike-desktop:~$ mount | grep -i 36CB
/dev/sdc1 on /media/36CB-D1A8 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
mike@mike-desktop:~$ touch /media/36CB-D1A8/wut.txt
touch: cannot touch `/media/36CB-D1A8/wut.txt': Read-only file system
mike@mike-desktop:~$ ls -l /media/36CB-D1A8/
total 4
drwx------ 3 mike mike 4096 2010-09-18 16:33 home
mike@mike-desktop:~$ chmod 775 /media/36CB-D1A8/*
chmod: changing permissions of `/media/36CB-D1A8/home': Read-only file system
mike@mike-desktop:~$ sudo chmod 775 /media/36CB-D1A8/
[sudo] password for mike: 
chmod: changing permissions of `/media/36CB-D1A8/': Read-only file system
mike@mike-desktop:~$

```

The device currently in question is definitely already mounted rw, but the system returns a Read-only flag.  I tried searching the net for the answer to this to no avail.

Help would be greatly appreciated!  :)

---

### Post by robsoles on 2010-09-20
Does that USB stick/device have a read only switch/tab? I feel a bit  silly asking but crazier stuff has happened - just smile and slap your  forehead if you find one and it's in the RO position right now!

I have been running both 32 and 64 bit installs since 9.04 and this  headache is not one of mine - none of my USB sticks (about 8 ) has  mounted anything other than RW, completely usable.

I read/heard that some of those USB sticks/devices have a software  function to be RO and it takes software from the manufacturer to 'flick that switch'.

---

### Post by gallifrey on 2010-09-20
try this:

sudo chown yourusername:yourusername /media/label-of-your-device

then:

sudo chmod 755 -R /dev/sdX where X is your device. You my also need to add the partition number, i.e. /dev/sdX1 etc. 

Try that, see how it goes. :)

---

### Post by snowveil on 2010-09-21
So, as I was typing out a reply to your suggestions (none of them worked, unfortunately), I figured it out :D


I switched over to tty1 and was getting tons of usb errors.  I tried plugging the drive into another port and it is working!

I guess I'll have to double check the usb headers from when I connected them to my mainboard upon installation.

Thanks for the suggestions guys :)

---

