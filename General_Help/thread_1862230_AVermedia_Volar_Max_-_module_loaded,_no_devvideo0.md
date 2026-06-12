---
title: "AVermedia Volar Max - module loaded, no /dev/video0"
date: 2011-10-16
forum: General Help
---

### Post by jonathan morales on 2011-10-16
After installing the driver from Avermedia's website, and confirming it's loaded with lsmod, I assume I'll have a device for the capture card in /dev named video0 as was the case when I had the usb stick in another computer running 10.04, but in this case it just isn't happening.

I've tried 9.10 and 10.10 to no avail. The module loads, but no /dev/video0 and mythtv is useless as it can't find a capture card to use. 

I wondered if there was a permission problem with udev so I logged in as root, and nothing changed. I'm out of ideas.

---

### Post by jonathan morales on 2011-10-16
Figured it out. The USB 2.0 controller wasn't enabled in the BIOS

---

