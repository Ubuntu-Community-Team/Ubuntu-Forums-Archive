---
title: "Need to find out what drivers I have installed"
date: 2010-12-17
forum: General Help
---

### Post by Mortesins93 on 2010-12-17
Hello,
I have an Xubuntu 9.10 which works fine with my Trust DS-3400D wireless keyboard and mouse. I tried installing on another partition Xubuntu 10.04, Ubuntu 10.04, Ubuntu 9.10 but none of them make my wireless keyboard work. So now, how can I find out what drivers my Xubuntu 9.10 is using to make my keyboard work? By the way, these drivers were installed by default because the keyboard worked as soon as I plugged it in.
Thanks in advance

---

### Post by Mortesins93 on 2010-12-24
So I got the list of all the drivers in my Xubuntu and on my other Ubuntu installation (on which the keyboard doesn't work). Now how can I install all of the drivers of Xubuntu on my other Ubuntu partition?

---

### Post by HermanAB on 2010-12-24
Once you know what they are, you can load them with the mod tools: lsmod, rmmod...

---

### Post by Mortesins93 on 2010-12-25
Thanks, but how can I load all of them at the same time? Is there a file I can copy from Xubuntu and paste it in to the other Ubuntu?

---

### Post by dino99 on 2010-12-25
[http://www.howtogeek.com/howto/17495/how-to-add-proprietary-drivers-to-ubuntu-10.04/](http://www.howtogeek.com/howto/17495/how-to-add-proprietary-drivers-to-ubuntu-10.04/)

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Mortesins93 on 2011-01-05
So I had a look at the two links Dino99 pointed out. So the first one is how to install proprietary drivers, but I don't want to install proprietary drivers since on my Xubuntu (where my keyboard works) there are no proprietary drivers installed so I guess there is a good open source alternative but I don't know which. Regarding the second link, can ndiswrapper be used for any windows driver? I thought it could only be used for wireless network cards.
I tried Puppy linux on my computer and the keyboard worked fine. During my Puppy linux session I copied down these three modules that were loaded which should have made my wireless keyboard work: 
ohci-hcd
ehci-hcd
usbcore
Now, how can I install them? Do I need to compile the kernel?
By the way, I tried installing Xubuntu 10.04 and for now the keyboard works.

---

### Post by Mortesins93 on 2011-01-05
So I searched the web a bit and I guess the  ehci-hcd and ohci-hcd modules is not what I am searching but maybe the usbcore module is the one.
Anyways my keyboard stopped working on my recently installed Xubuntu 10.04.
Hope you can help me find the right module.

---

### Post by amsterdamharu on 2011-01-05
Could you post your /etc/X11/xorg.conf ?
And check out what mods are loaded using this command:
```
lsmod
```
For usb devices:
```
lsusb
```

---

### Post by Mortesins93 on 2011-01-15
Thank you very much, ```
lsmod
``` was what I was searching for. Anyways I tried typing ```
gksudo mousepad /etc/X11/xorg.conf
``` in terminal and I got a blank page. It seems I don't have that file, is that possible? Here is what I have in /etc/X11 ```
axel@axel-laptop:/etc/X11$ ls -l
total 68
drwxr-xr-x 2 root root  4096 2009-10-28 21:14 app-defaults
drwxr-xr-x 2 root root  4096 2009-10-28 21:14 cursors
-rw-r--r-- 1 root root    14 2009-10-28 21:15 default-display-manager
drwxr-xr-x 6 root root  4096 2009-10-28 21:10 fonts
-rw-r--r-- 1 root root 17394 2009-06-23 00:57 rgb.txt
lrwxrwxrwx 1 root root    13 2010-07-16 17:59 X -> /usr/bin/Xorg
drwxr-xr-x 3 root root  4096 2009-10-28 21:14 xinit
drwxr-xr-x 2 root root  4096 2009-10-28 21:06 xkb
drwxr-xr-x 2 root root  4096 2009-10-28 21:07 Xresources
-rwxr-xr-x 1 root root  3730 2008-06-25 04:05 Xsession
drwxr-xr-x 2 root root  4096 2010-12-03 18:21 Xsession.d
-rw-r--r-- 1 root root   265 2008-06-25 04:05 Xsession.options
-rw-r--r-- 1 root root    13 2009-08-25 02:37 XvMCConfig
-rw------- 1 root root   601 2009-10-28 21:07 Xwrapper.config
axel@axel-laptop:/etc/X11$ 

```

---

### Post by amsterdamharu on 2011-01-15
you could check the /var/log/Xorg.0.log or any Xorg??.log that is recent. There is a line saying: "Using config file: " That might show you what X is using to configure your keyboard.

Did you find your keyboard with lsusb? What model is it according to Ubuntu?

---

### Post by Mortesins93 on 2011-01-15
So I checked a log but I did not find the "Using config file:". Should it be at the top? I did not manually search for it but the string was not found by mousepad.
I did not find out what model it is according to ubuntu but here is my lsusb output:
```

axel@axel-laptop:~$ lsusb
Bus 002 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0b05:170c ASUSTek Computer, Inc. WL-159g
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 07d1:3c03 D-Link System DWL-G122 802.11g Adapter [ralink rt73]
axel@axel-laptop:~$ 

```
I have four usbs. One has the wireless D-Link adapter which is listed, another one has a Trust usb hub which is also listed as Genesys Logic, another usb has a laptop cooler fan, and the last one is my wireless keyboard and mouse set. WL-159g should be the integrated wireless adapter, can it be listed in lsusb even though it is integrated? 
Anyways I tried loading the usbhid module on the other Ubuntu partition and now the keyboard works so I can say, even though I AM NOT 100% SURE, that the module I was searching for is: ```
usbhid
```

---

### Post by Mortesins93 on 2011-01-15
New update, after 3 seconds of deep thinking I realized that by typing lsusb after removing my peripherals one by one I could find out what my keyboard is listed as: ```
Bus 002 Device 005: ID 04fc:05d8 Sunplus Technology Co., Ltd
```

---

