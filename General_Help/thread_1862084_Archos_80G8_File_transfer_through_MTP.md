---
title: "Archos 80G8 File transfer through MTP"
date: 2011-10-16
forum: General Help
---

### Post by quinnten83 on 2011-10-16
Hi,
I just bought myself an Archos 80 G9 running Android 3.2.46 and I'm loving it so far, despite a few little niggles here and there.
At this moment, my biggest issue is that I can't easily transfer files to and from the tablet using the USB cable.
I was wondering if somebody could help me out with this one.
In the manual it says that you can use MTP to transfer files to and from your device, but they never mention which program you can use for that. I have installed a program gMTP from the repositories that is supposed to work with MTP devices, but it never gets recognized, the software does not find the tablet. Also the filebrowser does not see the tablet either. 
This leads me to my second issue, when I query the USB drivers, I can clearly see that the USB does see an Archos device:

```
home@home-pc:~$ lsusb
Bus 002 Device 006: ID 0e79:1508 Archos, Inc. 
```

The Kernel is also aware that there is an USB device on 006

```
[ 2380.316074] usb 2-1: new high speed USB device number 6 using ehci_hcd
[ 2573.160649] gmtp[3553]: segfault at 18 ip 0000000000416f7d sp 00007fff0b9c7af0 error 4 in gmtp[400000+1f000]
```

However gMTP gets an error.
I have no idea what that all means, but I was hoping that somebody might know how to get it working.
I'm using Ubuntu 11.10 (64 bits), right now I do file transfers through the wireless, but I won't always be able to do that.

Kind regards

---

### Post by p110011 on 2011-10-17
Hello quinnten83, saw that you also posted on archosfan. I'm surprised you got no answer yet. The only thing I read elsewhere was, to make sure debugging was off in the tablet.

I don't have an archos, yet, so I hope you can get this resolved.

---

### Post by pufinuntu on 2011-10-23
**Hi,**

**I think I've found a way to fix that problem... Actually it fixes the problem to every honeycomb device on Ubuntu (it's an english translation of that [solution]("http://www.frandroid.com/tutoriaux/71572_les-tablettes-sous-honeycomb-peuvent-etre-utilisees-montees-sous-linux/"))**

**First you have to enter that code in a terminal**

```

sudo apt-get install mtpfs
sudo mkdir /media/tablet (or whatever you want)
sudo chmod 775 /media/tablet 
sudo mtpfs -o allow_other /media/tablet

```**Then edit the file /etc/udev/rules.d/51-android.rules :**

```
sudo gedit /etc/udev/rules.d/51-android.rules
```**You must add the following lines **

```
 SUBSYSTEMS=="usb", ATTRS{idVendor}=="xxxx", ATTRS{idProduct}=="xxxx", MODE="0666", OWNER="_**_" #<_$$_> 
```The idVendor is the first number before the ":", the idProduct is the number after in 
*Bus 002 Device 005: ID 0e79:1508 Archos, Inc. *( So idVendor = 0e79; idProduct=1508 )

** = the name you use to log in
$$ = the name of your device or every name you want


**Last thing : run this comand in a terminal **

```
sudo chmod a+r /etc/udev/rules.d/51-android.rules
```[B]Plug your Archos 80 g9 on your computer. You will be able to browse your tablet.
Hope it will work for you !

A french ubuntu&archos fan [/B]

---

### Post by pufinuntu on 2011-10-23
Actually I think there is another problem with the rights... I cannot copy or paste something into the device or from the device... Maybe there is a fix with one of the chmod comand ? Sorry for that mistake.:(

---

### Post by dkohen on 2011-10-25
Change the 666 in the /etc/udev/rules.d/51-android.rules file to 777 and it works fine: 

SUBSYSTEMS=="usb", ATTRS{idVendor}=="0e79", ATTRS{idProduct}=="1508", MODE="0777", OWNER="your_name_here" #<tablet>

---

### Post by dkohen on 2011-10-25
Now i want to know how to run the mount and unmount commands automatically - any ideas?

---

