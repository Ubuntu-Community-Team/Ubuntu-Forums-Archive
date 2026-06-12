---
title: "Where are usb-serial.c and option.c"
date: 2010-10-30
forum: General Help
---

### Post by sportsdude81 on 2010-10-30
I need to make new drivers for a serial modem I am using, but for the life of me I can't find usb-serial.c and option.c.  I have the .ko files for both and when I look in 

```
/usr/src/linux-headers-2.6.32-24-generic/drivers/usb/serial
```

they're no where to be found.

I am running Lucid 64 bit.  Do I have to install a dev?  Any help would be much appreciated.

---

### Post by yabbadabbadont on 2010-10-30
You will need to install the kernel source package as the kernel headers package contains... wait for it... header files only.  :D

Install the package: linux-source

That should pull down the sources for the kernel you are currently using.  You will probably also need to install build-essential if you plan on compiling anything.

---

### Post by sportsdude81 on 2010-10-30
I already have both those packages installed.  I look in the folders where I thought they should be. I even did a 

```
sudo find / -name option.c
```

still nothing! I even install the USB dev files.

---

### Post by yabbadabbadont on 2010-10-30
Apparently the code has been refactored or something.  That file doesn't appear to be in the current kernel source tree...

[http://www.linuxhq.com/kernel/v2.6/36/drivers/serial/index.html](http://www.linuxhq.com/kernel/v2.6/36/drivers/serial/index.html)

Edit: but it is in the vanilla kernel 2.6.32

[http://www.linuxhq.com/kernel/v2.6/32/drivers/usb/serial/index.html](http://www.linuxhq.com/kernel/v2.6/32/drivers/usb/serial/index.html)

Edit2: but not in the most recent version of 2.6.32-25

[http://www.linuxhq.com/kernel/v2.6/32.25/drivers/usb/serial/index.html](http://www.linuxhq.com/kernel/v2.6/32.25/drivers/usb/serial/index.html)

---

### Post by sportsdude81 on 2010-10-30
I have the kernel

```
Linux Lucid 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:58:24 UTC 2010 x86_64 GNU/Linux
```

so I looked in there and they have the option.c, but not the usbserial.c. Where else could it be?  There has to be one because I have a usbserial.ko and that had to be compiled from somewhere.

---

### Post by sportsdude81 on 2010-10-30
So I'm pretty sure I found the right files to use from the website you gave me, but all the code they have there is patches and since I don't have an original source file it is pretty much useless to me. So if some one could upload the previous source or tell me where to find it because I have no idea where to find it.

---

### Post by sportsdude81 on 2010-10-30
Alright figured it out. after you install linux-source you have to go to /usr/src and there should be linux-source-2.6.32.tar.bz2, so once you unzip that all the source files should be in their proper place.

this should all be done as root.

```
apt-get install linux-source

cd /usr/src

tar -xjvf linux-source-2.6.32.tar.bz2
```

Hopefully this will save you the wild goose chase I just went through.

---

