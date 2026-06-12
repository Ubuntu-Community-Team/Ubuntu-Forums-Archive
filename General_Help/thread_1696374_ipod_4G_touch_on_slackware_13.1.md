---
title: "ipod 4G touch on slackware 13.1"
date: 2011-02-27
forum: General Help
---

### Post by sesnf86 on 2011-02-27
I have recently purchased an ipod touch 4g and i am trying to sync it with my laptop running on slackware 13.1.

So i looked around these links [http://ubuntuforums.org/showthread.php?t=1567271](http://ubuntuforums.org/showthread.php?t=1567271) and [http://everydaylht.com/howtos/desktop/iphoneipod-touch-on-linux/](http://everydaylht.com/howtos/desktop/iphoneipod-touch-on-linux/)

 and downloaded 


[libimobiledevice-1.0.4.tar.bz2]("http://www.libimobiledevice.org/downloads/libimobiledevice-1.0.4.tar.bz2")
[ifuse-1.1.1.tar.bz2]("http://www.libimobiledevice.org/downloads/ifuse-1.1.1.tar.bz2")
[libplist-1.3.tar.bz2]("http://www.libimobiledevice.org/downloads/libplist-1.3.tar.bz2")
[usbmuxd-1.0.6.tar.bz2]("http://marcansoft.com/uploads/usbmuxd/usbmuxd-1.0.6.tar.bz2")

I have created slackware packages using src2pkg and installed them on my system.
But when i do ifuse /media/ipod it gives an error 


> 
usbmuxd_get_device_list: error opening socket!
No device found, is it connected?
If it is make sure that your user has permissions to access the raw usb  device.
If you're still having issues try unplugging the device and reconnecting  it.
i am using root account while doing this.

when i do a lsusb | grep Apple it shows 

> Bus 002 Device 006: ID 05ac:129e Apple, Inc. So can anybody point out what i am doing wrong 

thanks

---

### Post by bls0n on 2011-02-27
I have them same question! Please help.

---

### Post by oldos2er on 2011-02-27
[http://www.linuxquestions.org/questions/forumdisplay.php?forumid=14](http://www.linuxquestions.org/questions/forumdisplay.php?forumid=14)

---

### Post by sesnf86 on 2011-02-27
@oldos2er

Thanks for the reply. I have read about the same problem with ubuntu users too so that is why i posted it over here hoping that someone may answer it. Anyways i had already posted it over there in the hardware section


@bls0n

Have you seen this [http://libiphone.lighthouseapp.com/projects/27916/tickets/174-ipod-touch-4g-not-detected](http://libiphone.lighthouseapp.com/projects/27916/tickets/174-ipod-touch-4g-not-detected)

> [INDENT]kerdosa updated this ticket at October 24th, 2010 @ 05:28 AM

This is a very simple problem. Ipod touch 4g has idProduct 0x129e.  Current usbmuxd has max idProduct 0x129a. It means usbmuxd will ignore  any ixxx device with idProduct 0x129a or higher. Just change this to  0x129f, then re-compile usbmuxd. Everything is working OK.

Modify two places:
1. In daemon/usb.h, change #define PID_RANGE_MAX 0x129a  to #define  PID_RANGE_MAX 0x129f. Recompile usbmuxd with cmake, install it.
2. Modify udev rules to recongize ipod touch 4g. In  /lib/udev/rules.d/85-usbmuxd.rules, change ATTR{idProduct}=="129[0-9a]"  to ATTR{idProduct}=="129[0-9ae]". Restart udev by "sudo restart udev".

Just plug in ipod touch 4g, enjoy it![/INDENT]You can get the  usbmuxd package here:
[http://marcansoft.com/uploads/usbmux...-1.0.5.tar.bz2]("http://marcansoft.com/uploads/usbmuxd/usbmuxd-1.0.5.tar.bz2")

You need cmake and libusb-devIt is not working for me as i am already using  [usbmuxd-1.0.6.tar.bz2]("http://marcansoft.com/uploads/usbmuxd/usbmuxd-1.0.6.tar.bz2")  but you can try it might work on your system if you are using an older version

---

### Post by sesnf86 on 2011-03-02
So i have managed to solve this, just posting it here for others.

After installing all the files mentioned above,  make sure you have created the usbmux user as specified in usbmuxd. Now do
> 
mkdir ~/ipod
This is the mount point for your ipod.

Then as root  type > usbmuxdThis was the problem in my case it may or may not be for you, try this if you are  facing problem while  mounting the ipod.  Now to mount the ipod > ifuse ~/ipod  and for unmounting > fusermount ~/ipodThis will give access to your ipods file system. I am still unable to sync my ipod with gtkpod though. If anyone knows how to sync please let me know

---

### Post by brainstormtrooper on 2011-03-02
I had a similar problem. To get gtkpod to work, I had to mount the iphone and then tell gtkpod where it was mounted - NOT the ~/.gtkpod folder. I can manage playlists and podcasts, but can no longer manage photos since moving to KDE (4.6) - don't know if that's related. 

I mounted my iphone to ~/.mount/iphone and set that path in the gtkpod settings under mountpoint then loaded the iphone.

---

### Post by sesnf86 on 2011-03-02
Well i am doing the same thing. I have mounted my ipod at ~/ipod. I can see all my files in gtkpod but whatever changes i do are not shown in my ipod. 

How do you sync your music ?

---

### Post by hatredman on 2013-05-02
Yes, usbmuxd looks like it's the problem. If fact, the problem is with systemd. Usbmuxd mus be mounted as root. The ols SysV init did that allright, but systemd does not like it and KILL usbmuxd. If you run it manually as root, everything works.

---

### Post by hatredman on 2013-05-02
And you can't sync music. Apple crypto thing will not let you. You NEED iTunes to do that, so you need a Virtual Machine with WinXP just to sync your music.

But for that to work, the issue with usbmuxd/systemd must be solved.

---

### Post by oldos2er on 2013-05-02
Old thread closed.

---

