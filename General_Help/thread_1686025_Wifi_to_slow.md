---
title: "Wifi to slow"
date: 2011-02-11
forum: General Help
---

### Post by sajansen on 2011-02-11
hi

i lik eto ask if thare is a way to reinstall a driver inubuntu... my wifi adapter is not working correctly, i will not connect faster than 1mb/s and it should be around 300 and on other computer it works fine so the usb stick is fine... on other networks it also connects with 1mb/s (network of the people living next to me...)

interface: 802.11 WiFi (wlan1)
driver: ar9170usb

thanks

---

### Post by ngrieb on 2011-02-11
Try downloading the wireless backport modules for the kernel you are using.

---

### Post by whatthefunk on 2011-02-11
Have you tried using ndiswrapper with the Windows driver?  That solved my wireless speed issues.

---

### Post by sajansen on 2011-02-12
oke..i have instaled the windows driver but i need to configuar it ore something...i dont get the configuration part...

sorry i`m still a noob :P

---

### Post by whatthefunk on 2011-02-12
How far did you get in the installation process?  Also, which type of device are you trying to connect with?  

This guide is one of the more helpful ones on the subject...
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by sajansen on 2011-02-12
i got as far as installing the driver, on a guide i tried the sad to configuar it with some tool that i could not fine... so i will try yours...

---

### Post by sajansen on 2011-02-12
still no luck...
device: Bus 001 Device 007: ID 0cf3:1002 Atheros Communications, Inc. TP-Link TL-WN821N v2 [Atheros AR9001U-(2)NG]

on the moment, connecting to an "g" network still works but is low (1mb/s on 60% signal), and the 'n" from myself wont even connect anymore. and it used still the same driver as before: ar9170usb

anyone an idea... Internet like this relay irritates me (A)...i think im the first ICT-er (meanly windows...figurers) with this kind of  Internet (A)

thanks

---

### Post by whatthefunk on 2011-02-12
Did you blacklist your old drivers?

---

### Post by sajansen on 2011-02-12
think that is the problem... i get an error on that step and the connecting issue is solved...i had mac adress filtering on and somehow it has a new mac adress ...ore something... but the driver is still a problem can you please give me the code to blacklist it for ubuntu 10.10...

the new drievr is : arusb_lhx
and the old is : ar9170usb

---

### Post by whatthefunk on 2011-02-12
Go to a terminal and type this:

```
sudo nano /etc/modprobe.d/blacklist.conf
```

It will ask you for your password and then open up a text editor.  There may or may not be anything in this file.  Paste in this at the bottom:

```
blacklist ar9170usb
```

Press Ctrl+x to save the file and once thats finished, reboot.  That should blacklist your old driver.

---

### Post by sajansen on 2011-02-12
Oke...The blacklist shure is working... But now the new driver aint working... 
Ndiswapper -l tels me that the new driver is installed, 
Device (0CF3:1002) present (alternate driver: ar9170usb) 
When i do Ndiswapper -a and fill the data in then it tels me thet the driver is alredy linked...

Ps sorry for spelling mestakes... No spelling control in this website if you visit it throu a iphone

---

### Post by whatthefunk on 2011-02-12
Hmmm...
Whats the exact name of your USB device?  These places might be able to help you:
[http://wiki.debian.org/ar9170usb](http://wiki.debian.org/ar9170usb)
[http://linuxwireless.org/en/users/Drivers/ar9170](http://linuxwireless.org/en/users/Drivers/ar9170)

---

### Post by sajansen on 2011-02-12
the device is : TP-Link TL-WN821N v2
ill try the links you gave me, ill let you know

---

### Post by whatthefunk on 2011-02-12
Have a look at this thread:
[http://ubuntuforums.org/archive/index.php/t-1052619.html](http://ubuntuforums.org/archive/index.php/t-1052619.html)

Those guys got it working with ndiswrapper.

---

### Post by sajansen on 2011-02-13
I have looked at it, but it sort of works bat the signal is still low... Well guess it cant be helpt...

---

