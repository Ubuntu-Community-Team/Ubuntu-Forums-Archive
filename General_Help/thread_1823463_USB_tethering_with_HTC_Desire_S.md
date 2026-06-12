---
title: "USB tethering with HTC Desire S"
date: 2011-08-12
forum: General Help
---

### Post by onako on 2011-08-12
After having a chance to read some posts related to connection of Android phones with Linux, I tried the USB tethering option. With the proper setting, the wireless network icon is replaced with two arrows, and there is a notification of connection. But, now I don't know how to get into the phone and browse/add/remove files. Which application should I use after I connect the phone? (I would like to use some GUI).

Note that I'm new to Ubuntu, and I need some help. I'm using Ubuntu 10.04 LTS - the Lucid Lynx.

Thanks

---

### Post by onako on 2011-08-12
After having a chance to read some posts related to connection of  Android phones with Linux, I tried the USB tethering option. With the  proper setting, the wireless network icon is replaced with two arrows,  and there is a notification of connection. But, now I don't know how to  get into the phone and browse/add/remove files. Which application should  I use after I connect the phone? (I would like to use some GUI).

Note that I'm new to Ubuntu, and I need some help. I'm using Ubuntu 10.04 LTS - the Lucid Lynx.

Thanks

(same post in Networking subforum. Reason: well, this is, perhaps, more of 'general help'. Apologies for any inconvenience.)

---

### Post by Carborundum on 2011-08-12
AFAIK, it is impossible to use an Android phone as a network tether and a storage device simultaneously. To access files on the phone, enable "USB Debugging" in "Settings>Applications>Development".

---

### Post by onako on 2011-08-12
After enabling USB debugging, the comp is still not reporting the storage device. But, in Computer, it is
recognizing the "Android phone" which cannot open. Any thoughts on how to resolve this?

---

### Post by haqking on 2011-08-12
You can however use the phone as a Wireless Hotspot and use the storage via USB cable.

Or at least i can with my Google Nexus which is HTC and currently running gingerbread.

---

### Post by onako on 2011-08-12
I do use the USB cable connection, but Ubuntu is not recognizing it properly. It only reports "Android phone" icon (cannot be opened). I found some ways to do resolve the problem, but it is very complicated. I doubt there should be some serious settings for this.

---

### Post by Carborundum on 2011-08-12
I should have mentioned, after enabling USB Debugging you need to manually tell your phone to connect to your computer before your computer can see your phone.

With USB Debugging enabled, connect your phone and your computer with the USB cable. Now go into the notifications area on your phone and click the "USB connected" notification. You should get a screen with an Android and a button saying "Connect USB storage". Click the button. Your computer should now automatically mount your phone and you should be able to browse files and directories.

---

### Post by haqking on 2011-08-12
Dont post multiple threads [http://ubuntuforums.org/showthread.php?p=11143806](http://ubuntuforums.org/showthread.php?p=11143806)

---

### Post by t0p on 2011-08-12
Do you really really want to do USB tethering, or would access via bluetooth be acceptable?

I've got a bluetooth dongle for my computer.  So if I want to transfer some music or whatever from pc to phone, I stick in the bluetooth dongle, and the bluetooth icon appears on my top panel.  I click on that, and opt to send files to device.  Sweet.

If this is utterly beside the point, please do not read the above.

---

### Post by s.fox on 2011-08-12
Please do not create duplicate threads. Thank you.

Threads merged.

---

### Post by haqking on 2011-08-12
> **t0p said:**
> Do you really really want to do USB tethering, or would access via bluetooth be acceptable?

I've got a bluetooth dongle for my computer.  So if I want to transfer some music or whatever from pc to phone, I stick in the bluetooth dongle, and the bluetooth icon appears on my top panel.  I click on that, and opt to send files to device.  Sweet.

If this is utterly beside the point, please do not read the above.

USB tethering and USB storage are different things.  USB tethering is for providing internet access from your phone through USB attachement to your computer.

If i was him i would use WiFi hotspot on my phone and then use USB or bluetooth for my file access.

---

### Post by elliotn on 2011-08-12
USB tethering is what I use for my internet with android, android works perfect with Ubuntu. to access files u need adb for system files

---

