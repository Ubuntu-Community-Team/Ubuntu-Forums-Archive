---
title: "hddtemp daemon not running"
date: 2009-12-19
forum: General Help
---

### Post by Lukas666 on 2009-12-19
Karmic 9.10 64bit. I installed all required tools: hddtemp, lm sensors, gnome Sensors Applet for temp monitoring. 

hddtemp works:

~$ sudo hddtemp /dev/sda
/dev/sda: SAMSUNG HE103UJ: 32°C

but when I start  Sensors Applet the hddtemp sensors is not available there (I have nvidia and cpu/mb detected). 

I guess it's because no hddtemp daemon is running. How can I make it work and start automatically?

It used to work out of the box on my previous build. But after I reinstalled everything (OS) from scratch it's different now (but hardware is exactly the same).

I'd like to avoid going to /etc/init.d if possible.

Thanks.

---

### Post by Lukas666 on 2009-12-19
> **Lukas666 said:**
> Karmic 9.10 64bit. I installed all required tools: hddtemp, lm sensors, gnome Sensors Applet for temp monitoring. 

hddtemp works:

~$ sudo hddtemp /dev/sda
/dev/sda: SAMSUNG HE103UJ: 32°C

but when I start  Sensors Applet the hddtemp sensors is not available there (I have nvidia and cpu/mb detected). 

I guess it's because no hddtemp daemon is running. How can I make it work and start automatically?

It used to work out of the box on my previous build. But after I reinstalled everything (OS) from scratch it's different now (but hardware is exactly the same).

I'd like to avoid going to /etc/init.d if possible.

Thanks.

Solution:

sudo dpkg-reconfigure hddtemp

---

