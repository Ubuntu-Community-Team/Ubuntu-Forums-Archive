---
title: "how to get info about a web cam"
date: 2011-12-05
forum: General Help
---

### Post by anoe on 2011-12-05
hi there, i've got ubuntu lucid and would like to know how to get info about my usb web cam, more specifically how many megapixels it's got. Tried with sysinfo but no luck. tx.

---

### Post by coldraven on 2011-12-05
If you are happy to use the command line then follow the instructions for Ubuntu here:
[http://www.techytalk.info/webcam-settings-control-ubuntu-fedora-linux-operating-system-cli/](http://www.techytalk.info/webcam-settings-control-ubuntu-fedora-linux-operating-system-cli/)

---

### Post by anoe on 2011-12-05
hi,

tx for the reply. I installed it, but i don't know how to get the megapixels with the info v4l2-ctl gives me... i went as far as asking for the formats and then the framesizes, but don't know what's the relationship with the resolution of the webcam... any help or link that talk about it?

tx again

---

### Post by no2498 on 2011-12-05
open a terminal type lsusb click enter
that should give you a number and name of your cam
use it in google to find what it is

---

### Post by crazy bird on 2011-12-05
> **no2498 said:**
> open a terminal type lsusb click enter
that should give you a number and name of your cam
use it in google to find what it is

What you mean can be found here: [https://sites.google.com/site/tipsandtricksforubuntu/system-tips/usb-device-id](https://sites.google.com/site/tipsandtricksforubuntu/system-tips/usb-device-id). The number provided by the command LSUSB is just a manufacturer/model number, it doesn't provide you of no more info than that.

---

### Post by liferules on 2011-12-05
Try installing cheese 

sudo apt-get install cheese

---

