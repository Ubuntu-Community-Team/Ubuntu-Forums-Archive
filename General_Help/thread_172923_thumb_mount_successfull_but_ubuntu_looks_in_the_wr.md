---
title: "thumb mount successfull but ubuntu looks in the wrong place"
date: 2006-05-09
forum: General Help
---

### Post by slush1000 on 2006-05-09
When I insert a thumb drive konqueror automatically opens and (tries to) mounts the drive and displays this warning:
---
An error occurred while loading media:/sda:
The file or folder media:/sda does not exist.
---

However, the drive IS successfully mounted and I can access it from /media/THUMB with no problems

How can I correct this so that it works, either with konqueror pointing to /media/THUMB on auto launch or changing the mount to be media:/sda.

Thanks.

---

### Post by Dr. Nick on 2006-05-09
Im not in kde at the moment so these may not be totally accurate.

Open up the K menu and go to system settings, look for disk and file systems dialog and peek around their. It controls where things are mounted to/from by making changes to the /etc/fstab file. if you post the ouptut of ```
cat /etc/fstab
``` it might help some

---

### Post by Omnios on 2006-05-09
```
---
An error occurred while loading media:/sda:
The file or folder media:/sda does not exist.
---
```

 Its trying to mount the pen to the Media/sda file which does not seem to exist. One solution would be to go the the media directory and create a sda directory or check fstab which will have something like /dev/hd?? /media/??? where media/??? is the file it tryes moutning to.

---

### Post by slush1000 on 2006-05-09
This is the output of the fstab file
```
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid,nouser 0 1
/dev/hda5 none swap sw 0 0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0 /media/floppy0 auto ,atime,noauto,rw,dev,exec,suid,user 0 0
```

There is no reference to either /sda or /thumb??

---

### Post by Dr. Nick on 2006-05-09
hmm... Was the usb stick plugged in when you ran the cat /etc/fstab? and did you see any mention of the usb stick in the disk/filesystems dialog of teh kde control center?

---

### Post by slush1000 on 2006-05-09
>   hmm... Was the usb stick plugged in when you ran the cat /etc/fstab? and did you see any mention of the usb stick in the disk/filesystems dialog of teh kde control center?

Yes, I had the usb stick plugged in when I ran the cat /etc/fstab and I also ran it with it unplugged as well and there was no difference. Also there is no reference to it in the disk/filesystem either :/

---

### Post by slush1000 on 2006-05-09
Thanks for all the quick replies.

OK, I just found something interesting but still need some advise.

In the file /etc/mtab
```
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /lib/modules/2.6.12-9-386/volatile tmpfs rw,mode=0755 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0
/dev/sda /media/THUMB vfat rw,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
```

The last line shows the /dev/sda code as you can see.

I then tried mkdir /dev/sda and recieved the following output
```
mkdir: '/dev/sda' exists but is not a directory
```

What should I try from this point??

---

### Post by Dr. Nick on 2006-05-09
Just a guess as I am not exactly sure why its doing that.
Try a mkdir /media/sda and change the mtab to  /media/sda instead of media/thumb


Hopefully someone who has a bit more knowledge can help out.

---

### Post by slush1000 on 2006-05-09
I got it working by following instructions on how to manually mount a thumb drive from a google search.

Well, apparently the mtab file auto appends itself so that file is not an issue. I made sure the 
```
/dev/sda /media/THUMB vfat rw,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=100
```
was removed from it and added to the fstab
```
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
```

everything works fine now.
Im still a little confused being a newbie but it works and im satisfied. Thanks for all the advise.

---

### Post by Dr. Nick on 2006-05-09
Glad you got it, The most annoying problems are the ones that shouldnt be their in the first place :) I may need this as my parents computer has started to screw up while mounting a thumb drive :rolleyes:

---

