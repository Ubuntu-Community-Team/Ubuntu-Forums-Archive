---
title: "Editing fstab"
date: 2011-04-10
forum: General Help
---

### Post by knknif on 2011-04-10
Im trying to get my extra media drives to auto mount at boot, having problems with it.  Does this line look right?

/dev/sdb    /media    auto    auto,user,noexec,rw,sync    0    2

The one thing I'm not sure about is the mount point, am I just putting '/media' or am I putting '/media/MKV' or whatever the name of the drive may be?

---

### Post by matt-fender on 2011-04-10
#Entry for /dev/sda1 :
UUID=7678346C78342CED    /media/sda1    ntfs    defaults,nls=utf8,umask=0222    0    0



this is how i've configured mine?

---

### Post by lmarmisa on 2011-04-10
> **knknif said:**
> Im trying to get my extra media drives to auto mount at boot, having problems with it.  Does this line look right?

/dev/sdb    /media    auto    auto,user,noexec,rw,sync    0    2

The one thing I'm not sure about is the mount point, am I just putting '/media' or am I putting '/media/MKV' or whatever the name of the drive may be?

You should create a directory in /media. For example:

```

sudo mkdir /media/MKV

```

Then use the path of this directory in fstab:

```

/dev/sdb1    /media/MKV    auto    auto,user,noexec,rw,sync    0    2

```

---

### Post by ~Plue on 2011-04-10
> **knknif said:**
> Im trying to get my extra media drives to auto mount at boot, having problems with it.  Does this line look right?

/dev/sdb    /media    auto    auto,user,noexec,rw,sync    0    2

The one thing I'm not sure about is the mount point, am I just putting '/media' or am I putting '/media/MKV' or whatever the name of the drive may be?
there are a couple of thing worth noting...

/dev/sdb is the device name and you wont be able to mount it. partitions have a number appended to the end (i.e. /dev/sdb1, /dev/sdb2...) 
to find the partition label, run *sudo fdisk -l (*lowercase L)
//an even better idea would be to use the uuid of the partition since the device label may change once you remove and re-insert the drive. this may not be a problem if its an internal harddrive though
to find the uuid, run[I] sudo blkid -c /dev/null
[/I]
/media is the parent directory of where usb devices and the sort gets auto mounted to, so it's not a good place to mount another partition.  i'd suggest mounting it to a subdirectory under /media such as /media/MKV (the directory should exist)

....
example of using disk label
/dev/sdb1 /media/Storage ext4 defaults 0 0

using the uuid
UUID=a968b7a4-1f22-490f-aae4-8a2c6b233525 /media/Storage ext4 defaults 0 0
....
links that might be helpful
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://www.ghacks.net/2009/01/03/understanding-linux-etcfstab/](http://www.ghacks.net/2009/01/03/understanding-linux-etcfstab/)

---

### Post by knknif on 2011-04-10
Ended up just using the UUIDs and they mount at boot now.  The only issue now is that it's listing each drive twice in the menu 'Places' along as within 'Computer'.  Not sure how to prevent/get rid of that.

---

### Post by ~Plue on 2011-04-10
> **knknif said:**
> Ended up just using the UUIDs and they mount at boot now.  The only issue now is that it's listing each drive twice in the menu 'Places' along as within 'Computer'.  Not sure how to prevent/get rid of that.
found an old bug report >> [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130)

not sure if it's related to this or not, but the work around there was to replace UUID=xxxx with 
/dev/disk/by-uuid/xxxx

---

### Post by knknif on 2011-04-10
Success, awesome!  

Thank you for the help.  Been trying to figure this one out for a while now and I just never had enough time to sit down and really work at it.

EDIT:  Now...How do I mark this as solved?  Probably pretty obvious but I'm not seein it lol.

---

### Post by ~Plue on 2011-04-10
glad i could help

see under **[COLOR=Red]Thread Tools[/COLOR]** at the top

---

### Post by sdibaja on 2011-05-24
> **~Plue said:**
> there are a couple of thing worth noting...

<<snip>>

/media is the parent directory of where usb devices and the sort gets auto mounted to, so it's not a good place to mount another partition.  i'd suggest mounting it to a subdirectory under /media such as /media/MKV (the directory should exist)

....
example of using disk label
/dev/sdb1 /media/Storage ext4 defaults 0 0

using the uuid
UUID=a968b7a4-1f22-490f-aae4-8a2c6b233525 /media/Storage ext4 defaults 0 0
<<snip>


Eureka! I finally got it! =D>

I got a device listing by running> sudo blkid -c /dev/null 
and then appended this to my fstab file, and it works!:
#
#----user input--- auto mount data drives 5/23/2011
#
#  Windows7
#/dev/sda1: LABEL="Windows7" UUID="4A5B809158A945C3" TYPE="ntfs"
UUID=4A5B809158A945C3 /media/Windows7 ntfs defaults 0 2
#
#  35GBFilesystem
#/dev/sda5: UUID="1852f2db-4099-40c2-a9cd-607c457b74ce" TYPE="ext4" 
UUID=1852f2db-4099-40c2-a9cd-607c457b74ce /media/35GBFilesystem ext4 defaults 0 2
#
#  data.docs
#/dev/sda6: LABEL="data.docs" UUID="1D11356F18CEC347" TYPE="ntfs"
UUID=1D11356F18CEC347 /media/data.docs ntfs defaults 0 2
#
#  S500back
#/dev/sdb1: LABEL="S500back" UUID="0282983E19313C6E" TYPE="ntfs" 
UUID=0282983E19313C6E /media/S500back ntfs defaults 0 2

Thanks! Peter
PS: [http://ubuntuforums.org/showthread.php?t=1666086](http://ubuntuforums.org/showthread.php?t=1666086) Post #4 was quite helpful too

---

