---
title: "HTC HD 7 not connecting via USB to 10.10"
date: 2010-11-29
forum: General Help
---

### Post by cmotdibbler13 on 2010-11-29
Hi all,

Having just got the new HTC HD 7 phone, I have tried to connect it to my computer via a USB but although it charges, Ubuntu does not recognize it as either a phone or as a disk drive.

I have no connection settings on the phone that I can change, as far as I can see and was wondering if any of you could help me mount the phone so that I can grab my photos.

Thanks for your help.

Jon

---

### Post by loell on 2010-11-29
that's because it's a bit new. ;)

what does it look like when you invoke **lsusb**?

---

### Post by cmotdibbler13 on 2010-11-29
What command do I use in terminal to get the required information?

Should I try lsusb-v?

or is there a program I can install to show this?

Sorry for being so dim, but as a dual booter I am still not used to using terminal for commands such as this.

---

### Post by loell on 2010-11-29
just **lsusb** , will do. :)

---

### Post by cmotdibbler13 on 2010-11-29
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 045e:04ec Microsoft Corp. 
Bus 002 Device 002: ID 064e:a103 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

that's what lsusb says in terminal.

---

### Post by 3rdalbum on 2010-12-29
Windows phones don't connect via USB Mass Storage. Microsoft doesn't want non-Windows users to use their phones.

However, you might be able to transfer photos via Bluetooth or by running a Samba server over WiFi.

---

### Post by tech-hero on 2010-12-29
> **cmotdibbler13 said:**
> Hi all,
 
Having just got the new HTC HD 7 phone, I have tried to connect it to my computer via a USB but although it charges, Ubuntu does not recognize it as either a phone or as a disk drive.
 
I have no connection settings on the phone that I can change, as far as I can see and was wondering if any of you could help me mount the phone so that I can grab my photos.
 
Thanks for your help.
 
Jon
 
 
Hi! have you tried installing WMstorage for PPC? i guess that will do. just turn it on and connect your device to your desktop. and it will function as a mass storage. it works with my HTC P3600. im just not so sure if it'll work with newer version.. but as long as it is run by windows mobile 5 and above, i think it'll work.

---

### Post by 3rdalbum on 2010-12-29
> **tech-hero said:**
> Hi! have you tried installing WMstorage for PPC? i guess that will do. just turn it on and connect your device to your desktop. and it will function as a mass storage. it works with my HTC P3600. im just not so sure if it'll work with newer version.. but as long as it is run by windows mobile 5 and above, i think it'll work.

Windows Phone 7 does not use PocketPC. It's a totally new, incompatible mobile OS.

---

### Post by tech-hero on 2010-12-29
maybe that's the case. we cant do anything about it, unless one will work on the windows mobile 7 side or the ubuntu side. :)

---

### Post by cmotdibbler13 on 2011-01-05
Thanks for all your help.

I guess I will have to wait until one of the clever people out there tries programming something to make them handshake.

Thanks again

Jon

---

### Post by 21android on 2011-03-02
If you are looking for a smartphone that can look after your wallet, then [HTC HD7]("http://www.cellhub.com/t-mobile-cell-phones/htc-hd7-black.html") is best buy at CellHub.com
This first window 7 Smartphone is avaliable now -a -days at throwaway prices and special discounts.The deals includes: Amex 

$25Gift voucher with new purchase as well as upgrading phone. On signing 2 years contract you get Free Phone and Free Nokia 

Bluetooth (worth $29.99). So Hurry! Only few days left for this great offer.

---

### Post by nitric on 2011-03-23
Hey guys, I got an HTC HD7 because I'm contracted with T-Mobile US and that was the best phone (as far as hardware specs go IMO) I must say I like being able to play games on it but you're right, updating it and adding music/getting videos off of it you can't do with Ubuntu alone! however I do not want to have to duel boot my system as I don't use windows for anything else.

BUT THERE IS A SOLUTION:

Get VirtualBox (not the one from the repositories as I believe that one still doesn't have USB support so just use your favorite search engine for their official site and get the version that has the USB controller.

Get a copy of Windows (XP Service Pack 3 or later, and no, it doesn't have to pass the windows genuine advantage as I have found out ;P)

Install Zune from Micro$oft

with your phone plugged in you can start up your virtual windows and connect to your phone, that's the only way I've found to get my videos off the phone, and add music to it :P

I for one am looking forward to the bright people over at xda-developers to come up with a way to replace the OS on this phone with Android.

Even though it says there is no way to expand the memory they have already found the 16gig microSD card and that you can upgrade it to 32gigs (doing so requires voiding the warrenty) so I know they'll find a way to hack the crappy (ok it's not all bad, the games are fun :P) OS off of it and replace it with an open source one.

IMO "Smart"phones are really becoming mini computers.

---

### Post by linuxsyst on 2011-05-30
Why you can install wine and run Zune on it?

---

### Post by nitric on 2011-08-24
I'm pretty sure Micro$oft Zune doesn't work with wine... [http://appdb.winehq.org/objectManager.php?sClass=application&iId=5741](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5741)

---

### Post by nitric on 2011-08-25
The HD7 doesn't give you any options on how to connect it to the computer, by default you can only access the videos and upload music through zune. you can get photos off of it by uploading them to facebook or emailing them to yourself but that is annoying as well and they are better sync'd through zune as well.

There is a way to have it show up as a "mass storage" device in windows by doing some registry tweeking ([http://www.knowyourcell.com/htc/htchd7/hd7userguides/686610/how_to_use_the_htc_hd7_as_a_usb_drive.html](http://www.knowyourcell.com/htc/htchd7/hd7userguides/686610/how_to_use_the_htc_hd7_as_a_usb_drive.html)) however I tried this and it shows the drive as 14 gigs (while it's a 16gig MicroSD card) and only shows the trivial folders of music, pictures, video, and does not show the Windows Phone 7 Operating system files which I believe are also stored on the MicroSD card (as you can upgrade it to a 32 Gig card and re-flash it with the OS by booting while holding down both volume buttons) I've wanted to take out the microSD and see if I could get to the core file system but haven't yet because I don't have a 0.4 torque screwdriver. (It also void's the warrenty to do so but I don't care about that I've been taking stuff apart since I was a kid :P)

---

