---
title: "Not sure how to run this command"
date: 2009-09-03
forum: General Help
---

### Post by jschille on 2009-09-03
So was perusing the forums about the low volume in Ubuntu and found an answer about how to fix it.
This was the answer
--------
adding to /etc/modprobe.d/alsa-base 

options snd-hda-intel model=3stack
----------

I am completely new to Ubuntu and have no idea how to use the command.
Any help is much appreciated.

---

### Post by ackanao on 2009-09-03
It looks like you need to add "**options snd-hda-intel model=3stack**" to your **alsa-base.conf** file - just open your text-editor (gedit) with "root" privileges:

```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

**/etc/modprobe.d** is a folder where **alsa-base.conf** file is located.

---

### Post by jschille on 2009-09-03
> **ackanao said:**
> It looks like you need to add "**options snd-hda-intel model=3stack**" to your **alsa-base.conf** file - just open your text-editor (gedit) with "root" privileges:

```
gksu gedit /etc/modprobe.d/alsa-base.conf
```**/etc/modprobe.d** is a folder where **alsa-base.conf** file is located.

Alright, got that. Opened up the file. Found all the options, should I just add **options snd-hda-intel model=3stack **to the list of current options? My current options are...

# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2

---

### Post by ackanao on 2009-09-03
Yes - just add **options snd-hda-intel model=3stack** line to your **alsa-base.conf** file and save changes.

---

