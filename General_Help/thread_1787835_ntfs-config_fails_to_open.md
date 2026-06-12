---
title: "ntfs-config fails to open"
date: 2011-06-21
forum: General Help
---

### Post by ppqq on 2011-06-21
Hi, I'm new to Linux!  Just came across the Ubuntu download page 4 days ago...

I've made a dual boot with winXP.  Most things are sorted out so that i can work, except .....

[SIZE=2]I'm trying to enter file write permissions for my ntfs drives using NTFS-config -I followed the ubuntu community documentation and it has installed, but it won't open! (there's no gui after password prompt)[/SIZE]

I would prefer using the tool rather than doing things manually!!
any ideas? thanks

---

### Post by ppqq on 2011-06-22
I found the answer to make the ntfs Config to work - but it surprises me why the documentation is not up to date for ubuntu 10.10

[http://www.ubunturoot.com/2010/11/fix-ntfs-configuration-tool-in-ubuntu.html](http://www.ubunturoot.com/2010/11/fix-ntfs-configuration-tool-in-ubuntu.html)

---

### Post by Morbius1 on 2011-06-22
Because ntfs-config is no longer maintained and does funny things to your system.

Consider the following: When you first run it it asks you is you want to enable write support for ntfs. Ntfs has had write support enabled by default since Hardy. 

Why doesn't ntfs-config know that and what exactly does it do when you answer yes?

---

### Post by ppqq on 2011-06-22
so what's the way to gain permissions on ntfs drives if not the config tool? because I also found this thread here in the community forum [http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263) which mentions ntfs-config.

As it is, I have got permissions on two internal drives, but then my ext drive lost permissions - well I could set that in ntfs-config but on linux start up it wants to see the ext drive and if I skip it because I didn't connect it to usb yet, lo and behold, it becomes damned from being mounted by Nautilus when I connect it after.

If there is a more stable way to mount ntfs drives now, please could anyone show me a thread, thanks!

---

### Post by Morbius1 on 2011-06-22
The most stable way to mount ntfs partitions is the Jedi way but you specifically stated that you would prefer to use a utility instead:
> I would prefer using the tool rather than doing things manually!!

---

### Post by coffeecat on 2011-06-22
@ppqq, friendly advice: listen to Morbius1. Morbius1 knows much more about NTFS in Ubuntu than most - possibly all - of us here. I concur with what he says about ntfs-config. It's old, unmaintained software that is best avoided. It confuses newbies, breaks systems and frightens the horses. The thread you linked to was started over three years ago. Time has moved on.

I don't understand what you mean by this:

> **ppqq said:**
> As it is, I have got permissions on two internal drives, but then my ext drive lost permissions - well I could set that in ntfs-config but on linux start up it wants to see the ext drive and if I skip it because I didn't connect it to usb yet, lo and behold, it becomes damned from being mounted by Nautilus when I connect it after.

Do you want to mount NTFS partitions on bootup? Because, if so, nothing stands up to what Morbius1 calls the Jedi way. If not, what is wrong with simply clicking on the NTFS partition in Places? You will experience no permissions problems if you do that.

---

### Post by ppqq on 2011-06-22
thanks, yes, I have taken the advice and removed ntfs-config.  Then I've  been looking at the fstab file, and the community Docu on it.  Looks  right, but I have a prob with the external drive.

I set the two main internal partitions to auto mount.  that works fine.

I set the ext drive (plus the internal Windows partition) to not mount at startup - the noauto option.

But they still want to - I get the Win partition mounted and Ubuntu asks  for the ext drive at start up.  I pass that with skip.  then in  Nautilus I click on the ext drive and it can't mount because the fstab  file is bad!

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    2
#Entry for /dev/sda5 :
UUID=d31f1057-fb41-4e60-8c0c-ab531c9ba24e    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sdb1 :
>>>>UUID=089C0DDA9C0DC364    /media/Expansion\040Drive    ntfs    rw,suid,dev, exec,noauto,nouser,async,nls=utf8,umask=000    0    0
#Entry for /dev/sda2 :
UUID=B04C39A04C3961F0    /media/FILES    ntfs    rw,suid,dev,exec,auto,user,async,nls=utf8,umask=0222    0    0
#Entry for /dev/sda3 :
UUID=F0A0533BA053080C    /media/VIDEO    ntfs    rw,suid,dev,exec,auto,nouser,async,nls=utf8,umask=0222    0    0
#Entry for /dev/sda1 :
>>>>UUID=EAC8F36AC8F33383    /media/sda1    ntfs    rw,suid,dev,exec,noauto, nouser, async,nls=utf8,umask=0222    0    0
#Entry for /dev/sda6 :
UUID=feccdb33-1220-48d8-8401-f9a94b7dbfe2    none    swap    sw    0    0

(Nautilus says line 9 and 15 >>>> are bad -the only lines with "noauto" which might be the crook here - and dev/sda2 is not found)

I expect you can see my errors??  should I change something?

is this the Jedi way per chance?? cheers for your help

---

### Post by Morbius1 on 2011-06-22
I will be delighted to show you the Jedi way if you are interested but let's see if we can fix what you've got:

> #Entry for /dev/sdb1 :
>>>>UUID=089C0DDA9C0DC364 /media/Expansion\040Drive ntfs rw,suid,dev, exec,noauto,nouser,async,nls=utf8,umask=000 0 0I'm assuming that the ">>>" are your notation - not even ntfs-config does that. Put a "#" sign in front of that line so that it looks like this and allow it to auto mount when turned on or plugged in:
> [COLOR=Blue]**#**[/COLOR]UUID=089C0DDA9C0DC364 /media/Expansion\040Drive ntfs rw,suid,dev, exec,noauto,nouser,async,nls=utf8,umask=000 0 0> #Entry for /dev/sda2 :
UUID=B04C39A04C3961F0 /media/FILES ntfs rw,suid,dev,exec,auto,user,async,nls=utf8,umask=02 22 0 0
#Entry for /dev/sda3 :
UUID=F0A0533BA053080C /media/VIDEO ntfs rw,suid,dev,exec,auto,nouser,async,nls=utf8,umask= 0222 0 0You have umask=0222 ( and in one case you have a space between the 2's ) which disables write. If you want to allow write then change it to umask=0000. 
> #Entry for /dev/sda1 :
>>>>UUID=EAC8F36AC8F33383 /media/sda1 ntfs rw,suid,dev,exec,noauto, nouser, async,nls=utf8,umask=0222 0 0Not sure what you are attempting to do here so just put a # sign in fron of the line so that it looks like this:
> [COLOR=Blue]**#**[/COLOR]UUID=EAC8F36AC8F33383 /media/sda1 ntfs rw,suid,dev,exec,noauto, nouser, async,nls=utf8,umask=0222 0 0[COLOR=Blue]**Notes:**[/COLOR]
* At a minimum you should run the following command and make sure the UUID numbers are correct:
```
sudo blkid -c /dev/null
```* Not even ntfs-config puts in all those options so you must have moved on to another gui utility. The newer utilities are newer not better.
* If you make any changes to fstab directly always unmount the partition you are working on first:
```
 sudo umount /media/FILES
```
And when you are done run the followinfg command to test for errors and remount the partition so you don't have to reboot:
```
sudo mount -a
```

[COLOR=Blue]**FYI:**[/COLOR] The Jedi way would have given you these entries in fstab assuming you wanted read / write access to these partitions and wanted to avoid an error message if you sent something to the trash:
```
UUID=B04C39A04C3961F0 /media/FILES ntfs defaults,nls=utf8,uid=1000,umask=000 0 0
UUID=F0A0533BA053080C /media/VIDEO ntfs defaults,nls=utf8,uid=1000,umask= 000 0 0
UUID=EAC8F36AC8F33383 /media/sda1 ntfs defaults,nls=utf8,uid=1000,umask=000 0 0

```

---

### Post by ppqq on 2011-06-22
sorry about the gap in the 2's, not in the fstab like that.  my error copying, as i had tried 000 but replaced 222 to paste here.

II think I was confused with auto/noauto, plus I thought that rw was needed to write to disk, and so I tried replacing defaults.  Anyway, the return of the Jedi has worked.. so far.  I used your lines, including for the external disk.  All drives present and no error messages in Nautilus.

....ok, on reboot the ext disk needs to be present to be mounted.  But ideally it should be mounted when I need it and i don't have to have it ready at every start up, so how can I do that?
its line is
UUID=089C0DDA9C0DC364    /media/Expansion\040Drive    ntfs    defaults,nls=utf8,uid=1000,umask=000 0 0

similarly, the partition 'sda1' doesn't need to mount at startup, only if I need it in Nautilus.  So what change can i make to its line?

UUID=EAC8F36AC8F33383 /media/sda1 ntfs defaults,nls=utf8,uid=1000,umask=000 0 0

also.... do the drive icons need to sit on the desktop and the launcher???

---

### Post by Morbius1 on 2011-06-22
> ....ok, on reboot the ext disk needs to be present to be mounted. But ideally it should be mounted when I need it and i don't have to have it ready at every start up, so how can I do that?
its line is
UUID=089C0DDA9C0DC364 /media/Expansion\040Drive ntfs defaults,nls=utf8,uid=1000,umask=000 0 0You don't want that line at all - that's why I had you put a # sign in front of it to tell the system to ignore it. Ubuntu automounts all external partitions when they are turned on or inserted.
> similarly, the partition 'sda1' doesn't need to mount at startup, only  if I need it in Nautilus.  So what change can i make to its line?

UUID=EAC8F36AC8F33383 /media/sda1 ntfs defaults,nls=utf8,uid=1000,umask=000 0 0
You don't want that line either if you don't want it to mount on boot. I had you place a "#" in front of that line as well. When you open up nautilus you should see the sda1 partition ( under some name - either the LABEL of the partition or even the uuid number ) listed and you can mount it by selecting it with the mouse.
>  also.... do the drive icons need to sit on the desktop and the launcher???     Is that something Unity does? I don't use Unity but I can tell you that you will get a desktop icon on any partition mounted to /media or somewhere in your /home directory. If the mountpoint is anywhere else then it will not be on the desktop. So let's say you do not want a mount icon for this partition:
> UUID=B04C39A04C3961F0 /media/FILES ntfs defaults,nls=utf8,uid=1000,umask=000 0 0Unmount the partition:
```
sudo umount /media/FILES
```Create a mountpoint somewhere else:
```
sudo mkdir /mnt/FILES
```Change the mountpoint in fstab to this:
> UUID=B04C39A04C3961F0 **[COLOR=Blue]/mnt/FILES[/COLOR]** ntfs defaults,nls=utf8,uid=1000,umask=000 0 0Save fstab and do the mount -a thing again:
```
sudo mount -a
```

---

### Post by ppqq on 2011-06-22
now i see !  I thought the # was part of a test, but that's how it needs to be properly.

brilliant, understood

---

### Post by ppqq on 2011-06-22
right, i made the new dir /mnt/FILES  and  /mnt/VIDEO and changed fstab, then sudo mount -a.

Now these two drives are found in the mnt dir in File System, and they don't show up in Places.  

I think I'll keep them mounting in media, then I have better access, plus I found that dconf-tools can stop drives showing on the unity launcher

sorry for taking your time with this

---

