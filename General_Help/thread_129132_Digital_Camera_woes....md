---
title: "Digital Camera woes..."
date: 2006-02-13
forum: General Help
---

### Post by matthinckley on 2006-02-13
OK I have a samsung Digimax A6 digital camera that uses a SD card for memory... I also have a RadioShack memory card reader.. works great for moving pictures onto the computer.. just put the card in the reader, plug into usb and voila.. pictures on my desktop.. 

anyways.. here's my problem..

My wife and I use the same computer.. different user accounts..

I have created a /home/share folder with ownership as root:users and permissions set at 777.. I have also set both our accounts as group users..

Symbolic links on both our desktops to the /home/share directory... this works great..

Unfortunately because the SD card is formatted as fat16.. what the Digital camera requires.. Linux sets permissions on everything on the card to 700... so when either one of us drags pictures from the camera into the /home/share folder.. the other can't even look at the pictures..

I've searched around found that since fat16 doesn't have a real permission structure linux just sets everything to a default and apparently the default on my computer is 700 but is there a way to tell linux to set anything fat16 formatted to say 770?

Thanks

Matt

---

### Post by aysiu on 2006-02-13
With FAT partitions and external media, the permissions are in how it's mounted.

I've found that putting something like this in /etc/fstab helps to make it mount with 777 permissions. Let's say the device shows up as /dev/sda1 and mounts at /media/sda1. Just create an /etc/fstab entry like this: ```
/dev/sda1 /media/sda1 vfat iocharset=utf8,umask=000 0 0
```

---

### Post by matthinckley on 2006-02-19
tried the fstab entry.. made absolutely no difference..

everything in my card has a permission of 700 and no matter what I can't change it until I move it to my hard drive.. I have been reading about udev rules.. don't know if this would have any effect..

[edit]

OK I watched a little bit closer and found the fstab entry did work.. however my usb device usually is /dev/sdb1 but sometimes is /dev/sdc1.. which was making my fstab entry for /dev/sdb1 irrelevant.. anyways this fix also puts a sdb1 device into my 'Computer' window all the time and if I was to add another fstab entry for /dev/sdc1 to alleviate the problem of the device changing.. it would just clutter up my 'Computer' window.. It seems to me that gnome-volume-manager uses udev to notify and automount devices.. wouldn't a udev rule be more effective?  If so, does anyone know what the udev rule would be or where it would be placed? 

I've read this page [here](http://reactivated.net/writing_udev_rules.html) and a lot of it is over my head.. I tried following the directions but it had no effect..

Thanks

Matt

---

### Post by matthinckley on 2006-03-02
OK just an update.. I did some more research and from what I have gathered gnome-volume-manager uses pmount to mount the drive and pmount defaults vfat drives permission to 700.. not good for me and my wife trying to copy files off a vfat drive into a shared folder...

even though we are in the same group. we cannot view any file the other copied into the shared folder..

apparently there is no way currently to change the way gnome-volume-manager runs pmount, although pmount does have cli options for setting permissions..

anyways, for now I  have implemented a workaround that involves a script that chmods the shared folder recursively to 777 and placed the script into roots crontab to run every hour..

not the prettiest of fixes but it works for what we need

Thanks

Matt

---

### Post by vdichev on 2007-12-03
Well, better later than never- I have another workaround, which might be a tad better. I rename pmount to pmount.orig, then create a pmount text file in the same directory (/usr/bin), then enter the following text:

```

#!/bin/sh
pmount.orig -u 007 $@

```

Then I change the permissions to be the same as the original pmount:

```

cd /usr/bin
chmod --reference=pmount.orig pmount
chgrp --reference=pmount.orig pmount

```

All needs to be done as user root, of course.

The described actions create a wrapper script with the same name as pmount, which invokes the original executable with the same command-line arguments, except that it adds one argument for the umask (umask controls default permissions). If you need to have not only people from your primary group have full access to the files, but everyone, change the mask to 000. If you want to give others just read access, try 002.

OK, the descriptions were a bit more detailed than what you need (apparently), but I figured it might be beneficial for newbies. Oh, and thanks for pointing me to gnome-volume-manager and pmount- this saved me some time.

---

