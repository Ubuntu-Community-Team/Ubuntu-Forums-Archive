---
title: "Scanner Mustek 2448TA Plus in Natty Failed to open device"
date: 2011-05-01
forum: General Help
---

### Post by Ramon444 on 2011-05-01
I have scanner Mustek BearPaw 2448 TA Plus
OS: Ubuntu 11.04 (fresh install)

i have downloaded [http://www.meier-geinitz.de/sane/gt68xx-backend/firmware/A2Nfw.usb](http://www.meier-geinitz.de/sane/gt68xx-backend/firmware/A2Nfw.usb) 
and copied it to /usr/share/sane/gt68xx/

then sudo chmod -R 0644 /usr/share/sane/gt68xx/A2Nfw.usb 

Also i have created file /etc/udev/rules.d/45-libsane.rules
with text:
ACTION!="add", SUBSYSTEM!="usb", DRIVER!="usb", GOTO="libsane_rules_end"

#Mustek Systems, Inc. BearPaw 2448 TA Plus
ATTR{idVendor}=="055f", ATTR{idProduct}=="021a", ATTR{product}=="USB Scanner", MODE="664", GROUP="scanner"

LABEL="libsane_rules_end"

i have created group scanner and added myself into it.

But it still don't work and gives me error:

Failed to open device 'gt68xx:libusb:006:004':
Invalid argument

When i run xsane under sudo it works. How to make it run without sudo ? I can't find when can be problem with rights.

PS. On maverick all worked fine.

---

### Post by Ramon444 on 2011-05-01
added more rights for group for this folder /usr/share/sane/gt68xx/
and now it works.

---

### Post by AlexVSharp on 2011-05-23
I must thank you for posting this since just moments ago I couldn't get my old Mustek Bearpaw 2448TA Plus device to work under Natty. :o

While your post isn't really formatted like a guide, with a bit of research I was able to implementing the files you mentioned. Now my scanner works under Ubuntu with no problems whatsoever. :D

Cheers~

---

### Post by Ramon444 on 2011-05-23
> **AlexVSharp said:**
> I must thank you for posting this since just moments ago I couldn't get my old Mustek Bearpaw 2448TA Plus device to work under Natty. :o
While your post isn't really formatted like a guide, with a bit of research I was able to implementing the files you mentioned. Now my scanner works under Ubuntu with no problems whatsoever. :D
I am happy, that my post helped you. :) If you have something to add, you can post here and i will be able to update main post.

---

