---
title: "Unable to Mount Galaxy Tab 2 7"
date: 2012-05-21
forum: General Help
---

### Post by Dan Again on 2012-05-21
I am not able to mount my Galaxy Tab 2 7 to transfer files...not trying to do anything fancy right now, just put music and stuff on it. I ran across several threads where people said they were having the same problem, but I'm not having much luck.

Initially, I didn't even see the device listed in Nautilus. The first thing I did was...

```
sudo apt-get install mtp-tools
```

Now I see the device in Nautilus, but when I try to mount it I get an error saying it can't lock the camera. I saw lots of people saying to go into Settings > Wireless and network > USB Utilities, but I don't see USB utilities anywhere.

Any help?

---

### Post by Dan Again on 2012-05-21
Bump. I've been using removable SD to transfer files, but it would be great to have the ability to do it via USB...that microSD card is hard to get out!

---

### Post by snafu_az on 2012-05-23
I haven't had any luck either.  I've installed mtp-tools, mtp-fs and gmtp.  None of them seem to work.

In the mean time I use andftp to transfer riles through wifi and I also found a samsung usb adapter [http://www.samsung.com/us/mobile/galaxy-tab-accessories/EPL-1PL0BEGSTA](http://www.samsung.com/us/mobile/galaxy-tab-accessories/EPL-1PL0BEGSTA) That allows me to connect a thumb drive directly to the tablet.

---

### Post by Dan Again on 2012-05-23
Oh well, so well...the microSD is an acceptable option for me at the moment, although that things is a pain to remove.

Have you given any thought to rooting your device? I'm assuming once it is running a custom ROM it will mount without problems...is that a valid assumption?

---

### Post by snafu_az on 2012-05-24
I'm a little shy about rooting the device. I'll keep searching for other solutions.

---

### Post by ikonjon on 2012-07-18
I've been using Swiftp for file transfer, running it on the tablet (as a mini temporary ftp server) and filezilla on the desktop to transfer the files.

Or, I've also used Andftp on the tablet.

No root needed for either, they're easy and fast.

I've tried updating mtp manually on unbuntu as well, and I too hate take that micro sd out...too easy to lose.

---

### Post by Dan Again on 2012-07-19
> **ikonjon said:**
> I've been using Swiftp for file transfer, running it on the tablet (as a mini temporary ftp server) and filezilla on the desktop to transfer the files.

Or, I've also used Andftp on the tablet.

No root needed for either, they're easy and fast.

I've tried updating mtp manually on unbuntu as well, and I too hate take that micro sd out...too easy to lose.

This is a great tip...had never tried this sort of thing before and it works like a charm. I am using WellFTP, but it's the same idea. Thank you very much!

---

### Post by edcrumly on 2013-01-07
As someone who found out the hard way, the first thing I found was the cord that comes with it doesn't work. You need an OTG cable from Amazon. This will transfer files and won't work as a charger. But it also allows you to connect to a USB hub, and connect other devices to the hub as well.

---

### Post by venomenus on 2013-01-07
Airdroid is quite a good app for managing your android device.
Works a charm. :)

---

### Post by Automat2 on 2013-01-16
> **edcrumly said:**
> As someone who found out the hard way, the first thing I found was the cord that comes with it doesn't work. You need an OTG cable from Amazon. This will transfer files and won't work as a charger. But it also allows you to connect to a USB hub, and connect other devices to the hub as well.
What's the difference between an OTG cable and the cable that comes with the phone or tablet?

---

### Post by edcrumly on 2013-01-18
> **Automat2 said:**
> What's the difference between an OTG cable and the cable that comes with the phone or tablet?

I believe they use two wire for charging one the it comes with, and diferent number and colors for the otg one. OTG does data travel, but usually not charging. Samsung, please stick to one cable for the whole schmozzle. Twenty bucks here, twenty there???

---

### Post by Automat2 on 2013-01-18
> **edcrumly said:**
> I believe they use two wire for charging one the it comes with, and diferent number and colors for the otg one. OTG does data travel, but usually not charging. Samsung, please stick to one cable for the whole schmozzle. Twenty bucks here, twenty there???
Ok. I didn't know.
 
I'll see if I can get hold of one of these wires.

---

### Post by clive littlewood on 2013-01-18
Hi

+1 for Airdroid (In the Play Store)

Works great for all transfers (Both ways) on my Galaxey S3

Clive

---

