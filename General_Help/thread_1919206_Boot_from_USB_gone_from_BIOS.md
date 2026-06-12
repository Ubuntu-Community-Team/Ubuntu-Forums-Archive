---
title: "Boot from USB gone from BIOS"
date: 2012-02-02
forum: General Help
---

### Post by drshahab on 2012-02-02
I made a bootable USB pen drive using unetbootin-windows from Ubuntu cd image on my Compaq Presario notebook CQ61. After the process completed it asked for reboot, I pressed OK button, but to my surprise I found that USB was gone from the boot menu. I have booted from a live USB pen drive on this same machine many times before, I tried resetting bios but still, no usb in boot menu!the notebook is otherwise working fine. searching the web I found only one mention of a similar problem at
[http://h30434.www3.hp.com/t5/Other-Desktop-PC-Questions/Boot-from-USB-gone-from-BIOS/m-p/1060071#M20012](http://h30434.www3.hp.com/t5/Other-Desktop-PC-Questions/Boot-from-USB-gone-from-BIOS/m-p/1060071#M20012)
with no answer.
can someone pl help?:

---

### Post by drshahab on 2012-02-03
I got the answer at another forum which I am posting here as it may be useful for someone else. He wrote

I have seen this on many occasions with Lenovo systems. An initial boot has the USB devise and following bootups don't. If you go into the bios you may find the option to add boot devises to the boot list. The USB devise for whatever reason gets defined as a USB devise but slightly different. I'm not sure what the unique distinction is but you would need to add that item to the boot list of devices.

What I did after reading the reply was

Although usb was gone from boot menu, & boot device list in BIOS I was able to find it under system configuration tab of BIOS where it was at the bottom of a list of usb devices with "!" mark, I was able to move it up the list & lo! it showed up in my boot menu again.

---

### Post by philinux on 2012-02-03
> **drshahab said:**
> I got the answer at another forum which I am posting here as it may be useful for someone else. He wrote

I have seen this on many occasions with Lenovo systems. An initial boot has the USB devise and following bootups don't. If you go into the bios you may find the option to add boot devises to the boot list. The USB devise for whatever reason gets defined as a USB devise but slightly different. I'm not sure what the unique distinction is but you would need to add that item to the boot list of devices.

What I did after reading the reply was

Although usb was gone from boot menu, & boot device list in BIOS I was able to find it under system configuration tab of BIOS where it was at the bottom of a list of usb devices with "!" mark, I was able to move it up the list & lo! it showed up in my boot menu again.

Exactly the same on my Asus mobo. If the usb stick remains plugged in it remembers bit if unplugged it goes to bottom of the list of drives.

---

