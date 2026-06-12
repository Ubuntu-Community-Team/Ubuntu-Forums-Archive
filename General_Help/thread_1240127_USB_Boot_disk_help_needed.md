---
title: "USB Boot disk help needed"
date: 2009-08-14
forum: General Help
---

### Post by Couto on 2009-08-14
I'm on Ubuntu at the moment and I have the ISO I want to install on Ubuntu.

I cannot use the 'USB Startup Disk Creator' because the file isn't for a CD (it's to big)

I refuse to use UNetbootin, and I know syslinux is good, because its what I used to install this Ubuntu here.

I've seen [http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html](http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html)

I just don't understand why it's so different from the Windows method.

On windows, you extract the iso to the usb, you take the isolinux folder, drag all its contents into the root of the usb, rename isolinux.cfg to syslinux.cfg and do 1 command in cmd. Something like: 
cd to the syslinux folder
cd to the win32 folder inside syslinux folder
syslinux -f :e

-- or something alone those lines. :confused:



Does anyone know how I'd do this the same way I just said using the Ubuntu Terminal?

cd Desktop 
cd syslinux (The syslinux folder is on my desktop)
cd linux (I think thats the Linux version of the file?? :confused:)
syslinux -f sdb1 (My USB mount is sdb1)

---

### Post by t0p on 2009-08-14
I don't know why you refuse to use unetbootin.  I use it lots, and it's pretty good.  But it's up to you...

To find out how to use syslinux, type into the terminal:

```
man syslinux
```

If you need clarification, feel free to ask here.

You may also find some useful info if you watch [this video]("http://www.podtrac.com/pts/redirect.avi/bitcast-a.bitgravity.com/revision3/web/hak5/0524/hak5--0524--usbmultipass--large.xvid.avi").  It isn't strictly about what you want to know, but it does cover installation to usb stick.

---

