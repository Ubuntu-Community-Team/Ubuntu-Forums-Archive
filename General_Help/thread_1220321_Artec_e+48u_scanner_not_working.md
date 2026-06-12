---
title: "Artec e+48u scanner not working"
date: 2009-07-22
forum: General Help
---

### Post by an4rk on 2009-07-22
I've been searching for hours on how to get this thing working. I previously had Hoary installed and the scanner worked fine.

_lsusb output_
Bus 007 Device 003: ID 05d8:4003 Ultima Electronics Corp. Artec E+ 48U

_sane-find-scanner output_
found USB scanner (vendor=0x05d8, product=0x4003, chip=GT-6816?) at libusb:007:003

scanimage -L does not find the scanner.

I have the appropriate driver file in the location identified in the artec_eplus48u.conf  -->  /usr/share/sane/artec_eplus48u

Any help would be appreciated.

---

### Post by an4rk on 2009-07-23
bump

---

### Post by an4rk on 2009-07-23
bump

---

### Post by an4rk on 2009-07-26
> **an4rk said:**
> bumpa

---

### Post by an4rk on 2009-07-31
Bump

---

### Post by drs305 on 2009-07-31
You seem to have hit a bumpy road.

I use this scanner. I'll tell you how I get mine to work. It seems you have done pretty much the same although the folders differ slightly:

```
sudo aptitude install sane  sane-utils # xsane should be installed automatically)	
lsusb  # make sure scanner is recognized (as you have done)

```
I had to pull the scanner driver from an old windows install. The artec driver was: windows/system32/drivers/Artec48.usb
```

sudo mkdir /usr/share/sane/artec_eplus48u # (or folder referenced in /etc/sane.d/artec_eplus48u.conf)
sudo chown -R yourusername: /usr/share/sane/artec_eplus48u
cp *your.artec.driver* /usr/share/sane/artec_eplus48u
```

Make sure the address from "lsusb" 05d8:4003 is correctly identified in artec's /etc/sane.d/artec_eplus48u.conf file.

I am on the road and away from my system with my scanner setup. This entry was made from my notes so your folder entries could be different. If the above doesn't work, let me know and in a few days I can check on my desktop computer and elaborate if necessary.

Good luck.

---

### Post by britstanger on 2011-08-26
Hi i seem to be having a similar problem. 

when i do ls usb it finds the scanner 

i have downloaded a driver from the artec website but i am not sure what to do with it now it is in my home folder and is called V3.0.0.exe

also the sane easy scan program finds the scanner but im assuming it needs to know where the driver is to use it.

thanks Leigh

---

