---
title: "blinking log-in screen and how to move files to usb in terminal"
date: 2010-02-06
forum: General Help
---

### Post by johnnysnotdead on 2010-02-06
Hello,

Last night when i tried to log onto my computer the login screen just blinked and would not allow me to log in. I run 9.10 on a Dell Inspiron E1505 and have had no real problems until now. I am able to run safe mode and have been trying for at least 3 hours to fix it. Now I am at the point where I just want to get all my important info off onto a few flash drives and reinstall ubuntu to see if that will work. Can anyone walk me through how to compress all of these files and get them on a flash drive? 

Thank you in advance for any help

---

### Post by theozzlives on 2010-02-06
> **johnnysnotdead said:**
> Hello,

Last night when i tried to log onto my computer the login screen just blinked and would not allow me to log in. I run 9.10 on a Dell Inspiron E1505 and have had no real problems until now. I am able to run safe mode and have been trying for at least 3 hours to fix it. Now I am at the point where I just want to get all my important info off onto a few flash drives and reinstall ubuntu to see if that will work. Can anyone walk me through how to compress all of these files and get them on a flash drive? 

Thank you in advance for any help

What have you tried? Sounds like a problem with GDM, or possibly a kernel panic.

---

### Post by johnnysnotdead on 2010-02-06
Well, I found these pages and did my best to do what they say, but with no luck.

[http://www.linuxforums.org/forum/ubuntu-help/113747-login-screen-blink.html](http://www.linuxforums.org/forum/ubuntu-help/113747-login-screen-blink.html)

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8571956](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8571956)

I am also a noob so a lot of this stuff doesn't make that much sense to me.

---

### Post by nerdy_kid on 2010-02-06
to move files to usb:
this is assuming you have one hard disk in your system

plug in the usb.  wait a sec...


```
sudo fdisk -l /dev/sdb
```


this will give a list of partitions and sizes on the usb.
remebber the name of the largest partition -- should be something like sdb1 or sdb2

```

sudo mkdir /media/usbdrive
sudo mount -t msdos /dev/sdb__(replace __ with the number you memorized in the previous step) /media/usbdrive

```

then just run cp -r against all the folders you want to copy. for example, your desktop dir:
```

cp -r ~/Desktop /media/usbdrive

```

then, when you are done:

```
sudo umount /media/usbdrive
```

remove the drive....
then

```
sudo halt
```

will shut everything down.

note that there is probably a way to get your display working, so i wouldnt recommend reinstalling until you've posted here for help.

---

### Post by johnnysnotdead on 2010-02-06
the one response on another thread said something about opening  xorg.conf. i am able to locate that file but i dont think i can view it on safe mode. is there a way to do this if it will help?

also in the same thread the kid figures out that he had a USB storage device plugged in and ubuntu wont boot if there is any kind of storage device plugged in. does anyone know how i can check to see if this is the cause, well not an external one but an internal one.

---

### Post by johnnysnotdead on 2010-02-06
or if is in fact a problem with the GDM or the kernel how would i go about fixing those or figuring out what went wrong?

---

### Post by nerdy_kid on 2010-02-07
id create a new thread...

---

