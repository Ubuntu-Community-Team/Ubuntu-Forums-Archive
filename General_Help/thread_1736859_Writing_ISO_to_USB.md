---
title: "Writing ISO to USB"
date: 2011-04-22
forum: General Help
---

### Post by Vulf on 2011-04-22
I want to create a bootable iso on usb, however not an Ubuntu or any linux distro on my USB drive. How would I go about doing that on Ubuntu 10.10?

---

### Post by piratebill on 2011-04-22
I use [MultiSystem]("http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/").  It works amazingly well for most the ISOs I've tested with.

---

### Post by KegHead on 2011-04-22
Hi!

You can burn iso images with unetbootin.

I've burned Fedora etc.

Should work.

KegHead

---

### Post by piratebill on 2011-04-22
> **KegHead said:**
> Hi!

You can burn iso images with unetbootin.

I've burned Fedora etc.

Should work.

KegHead

to my knowledge Unetbootin only works for linux based ISOs

---

### Post by Dutch70 on 2011-04-22
[[COLOR="Red"]http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/[/COLOR]]("http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/")

---

### Post by Vulf on 2011-04-22
The instructions seem to be for a Windows OS. I'm on ubuntu.

---

### Post by joberly on 2011-04-22
Can't you just use the Startup Disk Creator? (System -> Administration -> Startup Disk Creator)

It just wants an .iso, doesn't seem to care what's in that .ISO.

---

### Post by piratebill on 2011-04-22
You can always try to run [this]("http://www.intowindows.com/how-to-create-bootable-windows-7-usb-to-install-windows-7-from-usb-flash-drive-using-windows-7-dvdusb-tool/") in wine

---

### Post by Vulf on 2011-04-22
> **joberly said:**
> Can't you just use the Startup Disk Creator? (System -> Administration -> Startup Disk Creator)

It just wants an .iso, doesn't seem to care what's in that .ISO.

Actually it does care. This is the error I get:

```
Could not move syslinux files in "/media/OPERATION": [Errno 2] No such file or directory. Maybe "/media/disk" is not an Ubuntu image?
```

Not very useful.


> **piratebill said:**
> You can always try to run [this]("http://www.intowindows.com/how-to-create-bootable-windows-7-usb-to-install-windows-7-from-usb-flash-drive-using-windows-7-dvdusb-tool/") in wine

I'll try that now, although WINE is so terribly buggy and unstable. Have you tried this method?

---

### Post by piratebill on 2011-04-22
> **Vulf said:**
> 

I'll try that now, although WINE is so terribly buggy and unstable. Have you tried this method?

The latest wine is pretty good (not in the repositories).  And no, I've never tried it.  Although, I'd be very tempted to try.  If only I was at home right now I would.

---

### Post by Vulf on 2011-04-22
That program didn't work. An error comes up saying that some system components are missing (I'm guessing because WINE is just an emulator.)

```
Component Image Master API v2 for Windows XP and Windows 2003 (KB932716-v2) has failed to install with the following error message:
"ERROR_INSTALL_FAILURE "

The following components failed to install:
- Image Master API v2 for Windows XP and Windows 2003 (KB932716-v2)

See the setup log file located at 'C:\users\vulf\Temp\VSD635.tmp\install.log' for more information.
```

---

### Post by piratebill on 2011-04-22
Do you have the latest wine from [http://www.winehq.org/?](http://www.winehq.org/?)

---

### Post by Vulf on 2011-04-22
Yes, I believe so. 1.3

---

### Post by piratebill on 2011-04-22
other than setting up a virtual machine and doing there I am out of ideas. :/  heck even that sounds like a bad idea

---

### Post by Vulf on 2011-04-22
I'll just go grab my dad's win 7 notebook and do it on there. Thanks!

---

### Post by icouldmakeyousmile on 2011-04-22
Did you try Multisystem, like the 2nd post suggested? If so, what issues did you encounter? I've used it once to get a non-Linux ISO onto a USB, but I'm interested to know what it wouldn't work for.

---

### Post by Vulf on 2011-04-22
> **icouldmakeyousmile said:**
> Did you try Multisystem, like the 2nd post suggested? If so, what issues did you encounter? I've used it once to get a non-Linux ISO onto a USB, but I'm interested to know what it wouldn't work for.

Yes I tried Multi-System and that isn't working. I get this error:

```
Install Grub2: /dev/sdb1/
```

Also the link to Windows 7 tool doesn't work because I am not trying to boot windows 7. I am trying to boot a modified version of windows xp, not a standard OS.

---

### Post by wilee-nilee on 2011-04-22
From a win enviroment has worked every time for me.
[http://wintoflash.com/home/en/](http://wintoflash.com/home/en/)

---

