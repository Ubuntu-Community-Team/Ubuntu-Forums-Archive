---
title: "Want to install ubuntu on external HDD"
date: 2006-02-17
forum: General Help
---

### Post by Groto on 2006-02-17
I have never used linux so I don't want it as my main OS. How do I install ubuntu on my new 500gb lacie external hdd? I want to have a dual boot option of either windows xp pro or ubuntu. I'd prefer to have a firewire connection but if you can only use usb while booting that is fine too. Can someone help me please? I have the latest ubuntu cd.

---

### Post by MrCheese on 2006-02-17
Basically, if you fire up the install CD & it detects the external hdd ok you can install on it ok. If your system supports booting from the external drive, make sure you install the boot loader to it rather than your internal drive. Make a note of which drive (eg, /dev/hda, /dev/hdf etc) the installer sees the external drive as and tell the bootloader installer to put it there.

---

### Post by cotcot on 2006-02-17
This is not easy. I tried it several times. The closest info i found was [http://frontier05.blogspot.com/2006/01/installing-ubuntu-to-external-usb.html](http://frontier05.blogspot.com/2006/01/installing-ubuntu-to-external-usb.html)

---

### Post by frodon on 2006-02-17
A nice guide on the topic here : [http://doc.gwos.org/index.php/ExternalBreezyUSBDrive](http://doc.gwos.org/index.php/ExternalBreezyUSBDrive)

---

