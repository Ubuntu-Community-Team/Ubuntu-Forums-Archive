---
title: "USB drive not shwing up....."
date: 2011-05-31
forum: General Help
---

### Post by romain.astie on 2011-05-31
hi all,

I can not see my usb stick on the desktop. I have set the options for storage media to automount, and when I run lsusb in as terminal, the usb stick is there. It just seems as if ubuntu is not realizing that the stick is a storage device... I can acess the device in windows XP, so i know that it isn't broken. This appeared when I upgraded from Xubuntu 10.10 to 11.04. Any Help is welcome.

What should I do?

---

### Post by romain.astie on 2011-05-31
Hello?
Anyone??
I need truly speedy help with this....

---

### Post by jerrrys on 2011-05-31
not a fix, but a speedy work-a-round; download 'disk utility'  i have used this to get cameras (usb) to mount.

---

### Post by Toz on 2011-05-31
> **romain.astie said:**
> hi all,

I can not see my usb stick on the desktop. I have set the options for storage media to automount, and when I run lsusb in as terminal, the usb stick is there. It just seems as if ubuntu is not realizing that the stick is a storage device... I can acess the device in windows XP, so i know that it isn't broken. This appeared when I upgraded from Xubuntu 10.10 to 11.04. Any Help is welcome.

What should I do?

1. Do you auto-login? 

2. Open a terminal window and type in the following: ```
apt-cache policy usbmount
```Post back the results.

3. With the terminal window open, type in ```
tail -f /var/log/syslog
```Insert the USB key. Post back the information that is displayed in the terminal window.

---

### Post by tjeremiah on 2011-05-31
did you just install the recent updates? If so, im sure those updates have something to do with this problem because im having the same problem.

---

### Post by romain.astie on 2011-06-01
Great. Right when I plugged in the stick to try and fix the problem, ubuntu moved a** and recognized it. Thanks for trying to help ,anyways....

---

