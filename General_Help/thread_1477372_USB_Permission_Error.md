---
title: "USB Permission Error"
date: 2010-05-08
forum: General Help
---

### Post by kfcSmitty on 2010-05-08
Ever since I upgraded to Lucid Lynx I cannot write to my USB stick.

If I run sudo nautilus then I can copy files, but if I try to change the permission on the media drive it fails with the error

'You do not have the permissions necessary to change the group of "usb0".'

I had no issues prior to my upgrade and I really have no idea how to fix this. I've also tried chowning myself for the mounted directory, but that failed as well.


Any help would be appreciated.

---

### Post by g29115 on 2010-05-09
I have to say I am having a very similar problem. If I plug in a CF card from my camera, it pulls it up, and I can browse and copy the files off the card. I can't however, delete or move them off the card. When I try to go in as root to change the ownership to g29115 for usb or usb0 (where it seems to mount) it tells me I can't. I tried this in both a terminal and going out of X and logging into a console.

G.

ps- I can't even technically unmount it and get the icon to disappear off the desktop.

---

### Post by deusdiabolus on 2010-05-14
I am having the same issues...when I left my MP3 player connected to my desktop system on reboot, Ubuntu 10.04 placed it first in the list of USB devices instead of my large external drive, which meant I had to change locations for a lot of things (and re-read my music library for two or three programs).  Rhythmbox sees my MP3 player, but I can't edit files on it and I can't copy or delete files on it via Nautilus or anything else.  I don't seem to have any problems copying, deleting or modifying files on the large external, but I am worried that I might be corrupting files without knowing it (especially when writing MP3 tags).  When I pull up the PROPERTIES dialog for either the MP3 player or the external drive, Ubuntu "cannot determine the permissions" for either one.

---

### Post by invisiblewardog on 2010-06-09
I've just noticed this recently as well.  I've found a workaround for the time being until I can dig further:

**I'm far from an expert.  I'm just a hobbyist.***

I frequently use:

```
sudo bash
```

This is generally not recommended, as it will run all subsequent commands as root.  Be careful, and exit when you are done.

Really.

In my case, I determined my USB device was /dev/sdc and the partition was /dev/sdc1

I was drawing a blank so I checked for devices before and after plugging in the USB device:

```
root@qwerty:~# find /dev | grep /dev/sd
```

(If you don't know what those do, find will list the contents of /dev and grep filters it to only show those containing "/dev/sd")

```
kevin@qwerty:~$ sudo bash
[sudo] password for kevin: 
root@qwerty:~# find /dev | grep /dev/sd
/dev/sdc1
/dev/sdc
/dev/sdd
/dev/sdb5
/dev/sdb3
/dev/sdb2
/dev/sdb1
/dev/sdb
/dev/sda4
/dev/sda3
/dev/sda2
/dev/sda1
/dev/sda
root@qwerty:~# umount /dev/sdc1
root@qwerty:~# exit
```

Now click on "places" and the device you intended to access.  It should be mounted for you with proper permissions.  My 16GB thumb drive had no problems as far as I can remember.  Only seemed to happen after I started using my new Droid.

---

### Post by timgood on 2010-06-10
Try uninstalling and then re-installing pmount. Worked for me.

---

### Post by invisiblewardog on 2010-06-10
[http://ubuntuforums.org/showthread.php?t=1469499](http://ubuntuforums.org/showthread.php?t=1469499)

```
sudo apt-get remove usbmount
```

Sounds weird...but it worked.

---

### Post by limestone on 2010-06-10
Try to format the usb memory? or try this in terminal sudo chown -R yourusername /media/usb mount folder

---

### Post by g29115 on 2010-06-28
> **invisiblewardog said:**
> [http://ubuntuforums.org/showthread.php?t=1469499](http://ubuntuforums.org/showthread.php?t=1469499)

```
sudo apt-get remove usbmount
```

Sounds weird...but it worked.

Finally! This seems to have worked for me and I have not lost access to any of my USB devices that were working before. Now when I plug in a thumb drive it pops up, labels it correctly, and give me full rw access. Give it a try. Worst case, you can always reinstall it.

G.

---

### Post by JustJ on 2010-07-04
neither usbmount nor pmount were installed on this fresh ubuntu lucid system.


sudo apt-get install pmount

followed by a reboot fixed the usb mount issues for me.

---

### Post by radddi on 2010-09-24
> **invisiblewardog said:**
> [http://ubuntuforums.org/showthread.php?t=1469499](http://ubuntuforums.org/showthread.php?t=1469499)

```
sudo apt-get remove usbmount
```

Sounds weird...but it worked.

I'm seconing that. Thank you very much!! :popcorn:

---

### Post by wgbuntu on 2010-09-24
Same problem with bootable thumb drive.  Removing usbmount fixed the issue.  Have pmount installed.

---

### Post by doublewitt on 2011-05-03
> **invisiblewardog said:**
> [http://ubuntuforums.org/showthread.php?t=1469499](http://ubuntuforums.org/showthread.php?t=1469499)

```
sudo apt-get remove usbmount
```

Sounds weird...but it worked.

that worked for me too - THANKS

---

