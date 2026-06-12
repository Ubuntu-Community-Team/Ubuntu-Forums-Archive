---
title: "cannot open ConsoleKit session"
date: 2011-03-11
forum: General Help
---

### Post by jynyl on 2011-03-11
Since doing an update (Kubuntu 10.04), this message appears when attempting to log in;
> Warning: cannot open ConsoleKit session: Unable to open session: the permission of the setuid helper is not correct.


How do I fix this?
And what is a setuid helper?

After clicking ok on the above warning, the system logs in, but gives 2 error messages;
- removed sound devices
- KNetworkManager cannot start because the installation is misconfigured.  System DBUS policy does not allow it to provide user settings. contact your system administrator or distribution. KNetworkManager will not start automatically in future.

Please, any tips on solving this?

TIA

---

### Post by jynyl on 2011-03-11
It appears that the update process had trouble.  This seemed to help fix it;
```
sudo dpkg --configure -a
```

Then rerun the update commands.

---

### Post by eduardomps on 2011-03-21
thanks for posting, had the same problem after changing from gnome to kde (and messing around with the configs) and this solution worked

---

### Post by uelkfr on 2011-10-09
Hi, I have installed Wubu on Windows 7. After I went to system options -> Application installation and updating -> selected all packages and instructed to update them all - the process halted on linux-header updating, but I needed to go sleep already, so I made system shutdown. On next day I got problems with audio driver and this error message presented in this topic have appeared. After running your instruction I get this:
> 
&#1054;&#1073;&#1088;&#1072;&#1073;&#1072;&#1090;&#1099;&#1074;&#1072;&#1102;&#1090;&#1089;&#1103; &#1090;&#1088;&#1080;&#1075;&#1075;&#1077;&#1088;&#1099; &#1076;&#1083;&#1103; initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic
cryptsetup: WARNING: failed to detect canonical device of /host/ubuntu/disks/root.disk
cryptsetup: WARNING: could not determine root device from /etc/fstab
Warning: No support for locale: ru_RU.utf8
I only understand that root.disk is Wubu's disk image. From Windows side of view it is located D:\ubuntu\disks\root.disk. If I would setup Ubuntu in separate partion I think I wouldn't have this error, but I decided to use Wubu for simplicity :sad:

And question about root.disk. How I can be sure that some program will not fragment this file? I think if root.disk will get fragmented some horrible will happen, I don't use any defragmentator currently like Auslogic DiskDefrag ScreenSaver, only use default Windows 7 defragmentator and it is scheduled on Wenesday 1:00! How to add this file and swap.disk to exceptions so it not moved and not defragmented, like pagefile.sys? Or do Wubu done it for me?

Do I need to install something to be ru_RU.utf8 supported?

EDIT: after rebooting, my Windows 7 couldn't run without autorepair, only after long process of autorepair I could run Windows, but haven't checked for any file damage yet. I'm scared to run Ubuntu again :(

---

### Post by gerrie.keyser on 2011-10-28
This worked for me!

---

### Post by gerrie.keyser on 2011-10-28
> **jynyl said:**
> It appears that the update process had trouble.  This seemed to help fix it;
```
sudo dpkg --configure -a
```

Then rerun the update commands.
This worked for me! After interrupting my update (Kubuntu 11.04) all drivers seemed not to be working (wireless, cd-drive, usb ports, sound). Ran the command and everything back to normal now.

---

### Post by Llywelyn on 2011-11-11
Thanks for the fix. Worked for me after Kubuntu updates to 11.04 caused loss of wireless network and sound.

---

### Post by Mizpa on 2011-12-14
Thanks for listing this fix, I will give it a spin - I'm new to Ubuntu becuz Ubuntu usually crashes within a few days. This is the first Ubuntu (Kubuntu 11.04 installed) that has ever worked for more than a day or two with me ...... we'll see if it lasts! I got the Ubuntu 11.04 Linux Identity Starter Magazine which included not only the 32 bit and 64 bit disk, but it had a disk with multi-boots of Ubuntu, Kubuntu, Xubuntu, and Mythubuntu. I gotta say, this Kubuntu that I'm running has been flawless until I got the above message ;).

* Thanks, that worked swell!

---

### Post by teasplurt on 2011-12-28
> **jynyl said:**
> It appears that the update process had trouble.  This seemed to help fix it;
```
sudo dpkg --configure -a
```

Then rerun the update commands.

What exactly does this do?  It fixed all of my problems and then some.  Also, thanks!

---

### Post by ares1981 on 2012-01-10
Good Answer!
I just had the very same problem. This solution worked fine! Now everything is running again as it is supposed to. Thanks!

---

### Post by epolin on 2012-10-14
Dash, effective solution. Many thanks!

---

