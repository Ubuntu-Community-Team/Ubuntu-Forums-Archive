---
title: "help installing libusb"
date: 2009-12-07
forum: General Help
---

### Post by r16l26r36 on 2009-12-07
i need to install libusb and despite switching to ubuntu in september and being fairly computer savvy have no idea what the hell to do. any help with this matter would be highly appreciated.   i have 1.0.6 available from this site  [http://sourceforge.net/projects/libusb/files/libusb-1.0/](http://sourceforge.net/projects/libusb/files/libusb-1.0/)

---

### Post by lloyd_b on 2009-12-07
You don't mention which release you're running, but under Karmic (9.10), "sudo apt-get install libusb-1.0-0" will get you the 1.0 version of libusb.

I don't know whether this package is available in earlier Ubuntu versions - you can try that command and see what happens.

If you actually need 1.0.6, just unpack the archive ("tar -jxvf libusb-1.0.6.tar.bz2"), "cd" into the directory it creates, then "./configure", "make", and if everything goes okay "sudo make install".

Note: you'll need the "build-essential" package install to do the above.

Lloyd B.

---

