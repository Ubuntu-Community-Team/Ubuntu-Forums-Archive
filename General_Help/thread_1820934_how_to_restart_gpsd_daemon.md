---
title: "how to restart gpsd daemon?"
date: 2011-08-08
forum: General Help
---

### Post by sdowney717 on 2011-08-08
I noticed something.
USB GPS device is sending data to gpsd and port is /dev/ttyUSB0
everything works, foxtrotGPS, OpenCPN, etc...

If I unplug the LT-20 and plug it back in then
LT-20 reaquires signal and the port /dev/ttyUSB0 has data
BUT the gpsd daemon does not pick back up.
If I reboot gpsd is working. So the disconnect of the device and reconnect I suppose means gpsd needs to restart, so how do you do this?
Also I went thru using the dpkg-reconfigure gpsd and set it to startup automatically. But something must not be right

here is a screenshot showing opencpn receiving data on ttyusb0 but gpsd nothing at all

---

### Post by Cheesehead on 2011-12-06
Try 'service gpsd restart'
or 'pkill gpsd; gpsd /dev/ttyUSB0'

Sometimes gpsd and udev need a few seconds to clean up after you unplug the GPS dongle.

My system, for example needs about 10 seconds before I can plug it back in. If I'm too early, then /dev/ttyUSB0 is still busy, and the GPS gets mounted at /dev/ttyUSB1 instead.

---

