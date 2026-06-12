---
title: "iphone 3gs in xubuntu lucid?"
date: 2010-04-30
forum: General Help
---

### Post by AllRadioisDead on 2010-04-30
Hi,
I understand that iphone syncing works out of the box in Ubuntu lucid. I'm using Xubuntu lucid and I can't get my iphone to mount. How can I get my iphone to mount?

---

### Post by AllRadioisDead on 2010-04-30
Bump! :(

---

### Post by AllRadioisDead on 2010-04-30
Bump! Sorry, but I'm leaving in a couple of hours and need this to work for the weekend.

---

### Post by AllRadioisDead on 2010-04-30
Bump!

---

### Post by AllRadioisDead on 2010-04-30
Bump!

---

### Post by OziOscar on 2010-05-05
I'm having the same problem. 

I plugged the iPhone 3GS in under 9.10 and it appeared as an icon on the desktop, but when clicked it showed another NFS share. Go figure. 

I've upgraded to 10.04 and it does not mount at all. 

'lsusb | grep Apple' proves that it is plugged in and is present. It is possible to retrieve the looooong serial number,via 'lsusb -v | grep -i iSerial' but I still can't mount it.

'ifuse /media/iPhone' gives the error "No device found, is it connected? If it is make sure that your user has permissions to access the raw usb device. If you're still having issues try unplugging the device and reconnecting it."

Sometimes, plugging the iPhone 3GS in after a reboot gives a dbus timeout error (sorry, don't have the precise text to hand). 


Any hints, anyone? I'm sorry, but I don't know where to start looking to find what's broken and to fix it.


Cheers - Ozi.

---

### Post by OziOscar on 2010-05-06
Forgot to mention, am already in the fuse and plugdev groups, so it's not likely a groups-based permissions problem. 

Anyone have any ideas, please?

Cheers - Ozi.

---

### Post by OziOscar on 2010-05-06
Sorry - forgot to mention that I'm a regular ordinary Ubuntu user and not a Xubuntu or other kinky variant thereof user. 

Plain old Ubuntu. Regular, off the rack, good old happy Ubuntu and for rather more releases than I would care to mention. 

Does that make it easier?

Or are the OP and myself the only two people in the Ubuntu world to experience a non-mount condition? I kinda doubt that... somehow. 

Hoping to find some encouragement or preferably some suggestions to rectify the problem. 

Cheers - Ozi.

---

### Post by cseibert on 2010-05-10
Same issue here. I don't see it in /media.

---

### Post by xtian88 on 2010-06-21
Having the same problem. I see the iPhone in Gigolo. Double click it and then it shows another icon for the iPhone, a total of two. Both Banshee and Rhythmbox (which supports iPhone syncing) are not recognizing it. It used to work when I was using UNR but it stopped in Xubuntu. 

This is the only reason why I am keeping my Win7 partition and I am itching to remove it.

---

