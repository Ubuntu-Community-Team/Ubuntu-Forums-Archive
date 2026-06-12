---
title: "how to install this??"
date: 2006-04-20
forum: General Help
---

### Post by Dutchbull on 2006-04-20
hi how can i install this software? this is in the dir:


accel.c  hwcfig.h  lcd.h               tbl1622a.h  viafb.modes
accel.h  hw.h      lcdtbl.h            tbl1622.h   via_i2c.c
chip.h   iface.c   Makefile            tbl1625.h   via_i2c.h
debug.h  iface.h   Makefile_24.kernel  tv.c        viamode.h
dvi.c    ioctl.c   Makefile_26.kernel  tv.h        vt1622a.c
dvi.h    ioctl.h   readme.txt          viafbdev.c  vt1622.c
hw.c     lcd.c     share.h             viafbdev.h  vt1625.c

---

### Post by Jagot on 2006-04-20
Make sure you have the build-essential package installed.  If not, then:

sudo apt-get install build-essential

Change to that directory, then:

./configure
make
sudo make install

---

### Post by Dutchbull on 2006-04-20
if i want to do the Make and sudo make install  it says

root@DS3D:/home/michael/Desktop/Linux# sudo make install
Makefile:135: *** Linux kernel source not found.  Stop.

what now?

---

