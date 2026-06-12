---
title: "New to Ubuntu. Need help with sound issue"
date: 2009-09-11
forum: General Help
---

### Post by Mordekka on 2009-09-11
I have just installed Ubuntu, and really have no idea what I am doing.

Here is my problem. My headset and microphone jacks in the front of my computer are not functioning in Ubuntu. 

Any ideas??

Also I have no idea where to find the Ubuntu equivalent of Windows "Device Manager"

---

### Post by wobin77 on 2009-09-11
device manager in ubuntu is something like :
for a list of devices found on usb
```
 lsusb
```
for a list of devices found on pci
```
lspci
```

For your headphone: is the sound turned on for it? (right click sound icon if i remember correctly)

---

### Post by sharath0007 on 2009-09-11
On what system have you installed ubuntu? (configuration)?

Check the sound settings in the alsa mixer

---

### Post by Claus7 on 2009-09-11
Hello,

first of all: welcome to the forums. I hope that many of your answers will be answered here. Have in mind that the more details you give, possibly the better the answers you 'll receive.

Now, which is your system? Do you have one sound card? Two? Also, which is your os (hardy, jaunty)?

Do you have any experience with terminal? The first thing you can do it to open sound options from the icon of sound in the panel. There you could see some things about sound and configure some options.

Regards!

---

