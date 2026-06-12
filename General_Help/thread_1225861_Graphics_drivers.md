---
title: "Graphics drivers"
date: 2009-07-29
forum: General Help
---

### Post by Basham on 2009-07-29
Running 9.04 purged all drivers and need some new ones. I'm very new to Ubuntu and could also use some help in installing said drivers. Thanks!

---

### Post by eddiemolko on 2009-07-29
what kind of graphic card are you ussing?? nvidia? ati?

---

### Post by Basham on 2009-07-29
Forgot to mention that...ATI Radeon X1300

---

### Post by eddiemolko on 2009-07-29
take a look in System>Administration>Hardware Drivers.

I'm almost sure that there will be the drivers you need.

---

### Post by Basham on 2009-07-29
none listed in hardware drivers

---

### Post by eddiemolko on 2009-07-29
what version of ubuntu do you have?

---

### Post by Basham on 2009-07-29
9.04 Jaunty

---

### Post by eddiemolko on 2009-07-29
maybe this will help you [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide")

---

### Post by 3rdalbum on 2009-07-29
The graphics card driver was removed for a good reason: ATI's latest driver doesn't support the X1300, and their old driver doesn't work with the new version of Xorg that's in Ubuntu 9.04.

So, either you could settle for the open-source graphics driver that is already in use (which might not give you 3D) or you could try buying a newer graphics card that is supported by the latest ATI driver.

---

### Post by Basham on 2009-07-29
I'm still sort of in the dark...

---

### Post by 3rdalbum on 2009-07-29
> **Basham said:**
> I'm still sort of in the dark...

The only driver you can use with your card, is already installed and in use. It is the open-source driver.

Your options are:

1. Live with the open-source driver.
2. Buy a new graphics card, that is supported by the current ATI or Nvidia proprietary drivers
3. Revert to Intrepid and use the old ATI proprietary driver.

---

### Post by Basham on 2009-07-29
I understand that I have to live with an open source driver but I need suggestions and instructions on how to load one...

---

### Post by NormanFLinux on 2009-08-03
The graphics card works fine. The open source drivers will work but the xorg.conf file has to be edited to force Ubuntu to use the installed ATI driver and then you get 3D effects. Its a shame Ubuntu removed its graphics card GUI configuration tool. Still, the xorg.conf file rarely needs to be edited since normally autodetection is quite good. It just doesn't always list the correct driver.

---

### Post by realzippy on 2009-08-03
[http://ubuntuforums.org/showthread.php?t=1229145](http://ubuntuforums.org/showthread.php?t=1229145)

..seems if they made it (ATI fglrx+9.04) by downgrading xorg to 1.5...

---

