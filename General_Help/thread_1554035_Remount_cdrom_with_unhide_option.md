---
title: "Remount cdrom with unhide option"
date: 2010-08-16
forum: General Help
---

### Post by evo9 on 2010-08-16
I'm trying to install WoW on my Ubuntu machine and I'm having trouble  right off the hop. I'm using an install DVD thru wine and it says since  the Installer.exe is hidden I need to remount my drive with the unhide  option on.

I'm following this guide [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

This is the part of the guide I'm getting stuck at

[COLOR=Olive]**Note** that on some WoW DVD's the  installer  executable is hidden and you need to re-mount the disc with  the  'unhide' option. To do this type in a terminal:
  sudo umount /dev/cdrom
  sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/[/COLOR]

The unmount part works just fine but when I go to remount the drive it gives me this error:

[COLOR=Olive]mount: mount point /media/cdrom0/ does not exist
[/COLOR] 
I'm probably just being a complete noob and missing something obvious  here, so if someone could point out what it is that would be quite  helpful. Thanks!

---

### Post by prshah on 2010-08-16
> **evo9 said:**
> 
  sudo umount /dev/cdrom
  sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/[/COLOR]

You probably do not have the /media/cdrom0 directory. Check with ```
ls /media
```

So:

a) Either create the /media/cdrom0 directory ```
sudo mkdir /media/cdrom0
```

OR (Recommended)

b) Use an existing, suitable directory from /media (Eg /media/cdrom)

Please post back if you need more details.

---

### Post by evo9 on 2010-08-16
That was extremely helpful thank you very much.

---

### Post by fortyseven05 on 2011-06-20
hey, i know this is an old thread, but i ran into the same problem. i made the directory /cdrom0 and was able to remount unhidden, however, im not unable to run the install.exe. i AM, however, able to run the .exe for directX, which is on the same dvd.  when i try to run the Install.exe, my computer tries to run it the cd rom drive spins up to what sounds like full speed, but stays there with no onscreen action until i eject the disk, at which point wine gives me:
   "No installer data could be found. If this problem persists, please contact Blizzard Technical Support."
   obviously blizzard is going to be less than no help, so...
           any ideas?   sorry for rambling lol

---

