---
title: "What tte F?????"
date: 2011-07-31
forum: General Help
---

### Post by bradlees on 2011-07-31
I am about to give up. I have 2 hds, one 150g the other 80g. Both have XP operating on them know. I would like to load ubuntu onto the smaller drive and use both os'es. 

I can't seem to get ubuntu onto the hd when I have it connected as a stand alone drive. Live CD, wubi, and the USB all fail. I can format this drive if need be or install alongside of xp. With the cd it either freezes, gives a message about a missing ntldr or some linux error message about mounting.
 
The USB does not do anything, and the wubi installs then goes to restart and it boots right back into xp.

What f'ing gives? why can't I take a fresh hard drive (rather an old, re-formatted, blank hd) and install ubuntu?

Thanks,

Ben:confused::confused:

---

### Post by Wim Sturkenboom on 2011-07-31
Have you verified the MD5 sum of the download?
Have you tested the disk for defects (option somewhere in a menu when you boot from CD)

---

### Post by bradlees on 2011-07-31
I have not verified the md5sum; I don't know how to. I will look into this. I did run a check on the discs to check for problems on a couple of my discs, not all of them and they came back fine on the ubuntu install screen, but that's as far as it went.:guitar:

---

### Post by pqwoerituytrueiwoq on 2011-07-31
[http://www.pc-tools.net/win32/md5sums/](http://www.pc-tools.net/win32/md5sums/)
you can use that to get a md5sum
if you used a torrent download the iso should be good as torrents verify peace piece they get
i always burn on the slowest speed my disk drive allows
you may need to go your boot menu (Asus uses F8****) push it during post i think my laptop uses F2 or F10 to get to the boot menu 
select usb to boot

---

### Post by bcbc on 2011-07-31
The CD and USB failure may be a bad burn or other setup problem. This page gives good instructions on how to create these: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

As for Wubi rebooting straight into Windows, you'll need to right click on My Computer, Properties, Advanced, Startup & recover settings, and make sure the time to display operating systems is set to 15 or 30. Sometimes it's set at 0 so it boots the default automatically.

Sometimes (not as common) the boot.ini entry for Ubuntu is missing. If the default OS dropdown doesn't show Ubuntu then this is the case. (PS don't change the default to Ubuntu).

But I suggest - if you want a direct install - try to recreate the USB and use that to install direct. Wubi is great for trying out and easy to uninstall if you decide you don't want it.

---

### Post by bradlees on 2011-07-31
I cannot get my pc to boot with the usb. I have checked in bios that usb is enabled. I assume the generic storage device refers to my usb in my boot menu?  There isn't anything else it could be. Also, the bios doesn't refer to any specific location (f) for usb booting?

---

### Post by bcbc on 2011-07-31
> **bradlees said:**
> I cannot get my pc to boot with the usb. I have checked in bios that usb is enabled. I assume the generic storage device refers to my usb in my boot menu?  There isn't anything else it could be. Also, the bios doesn't refer to any specific location (f) for usb booting?
You have to check the boot order - if the hard drive is above usb devices, then it won't work. But most bioses also have a boot options key that will give a menu and you can override the boot order on the fly - and select USB from there. e.g. F12 works on mine (but the key probably differs on different computers.)

If you computer doesn't support this then CD's the other option.

---

