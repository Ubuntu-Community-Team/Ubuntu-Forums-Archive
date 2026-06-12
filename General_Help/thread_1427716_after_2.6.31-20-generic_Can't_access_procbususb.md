---
title: "after 2.6.31-20-generic Can't access /proc/bus/usb/"
date: 2010-03-11
forum: General Help
---

### Post by emptybottle on 2010-03-11
I'm using my GPS with ubuntu and after 2.6.31-20-generic upgrade I can't use this sentence: sudo mount -t usbfs none /proc/bus/usb/ . Error: "mount: mount point /proc/bus/usb/ does not exist"

I tried using root on nautilus but can't access or see the usb folder. I have no problems at all with 2.6.31-19-generic. 

I need my chart program (opencpn) for my boat and this is quite annoying. Can anybody please help?

( I use three sentences to enable my GPS: 

gksudo modprobe garmin_gps
sudo mount -t usbfs none /proc/bus/usb/
sudo gpsd /dev/ttyUSB0 )

---

### Post by cagney on 2010-03-20
If you are on Ubuntu 9.10, and have gpsd installed, all you have to do to get gps going is to plug in the gps connection, provided you have the following set in OpenCPN:
ToolBox => GPS => NMEA DAta Source == Network GPSD

The instructions you are following, was a workaround when gpsd did not start automatically. This is now fixed.

---

### Post by BramWillemsen on 2010-03-20
My flgrx drivers broke again during the transition of 2.6.31-19 to -20. I chose to just use the 2.6.31-19 kernel instead. By fixing the kernel you wont have things breaking down like that anymore. Of course you would miss out on security updates and such. But i guess if you are an end-user like me you will save yourself a whole lot of problems by just selecting and sticking to a kernel version that works good for you. 

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) describes how to configure grub2. 

Then reboot. the option 'uname -r' will display the kernel version, make sure it really is the version you wanted (maybe you made a mistake). 

DISCLAIMER: I do use ubuntu for a while and i found some things that work convenient for me. I'm in no way an expert user so in case of doubt please consult someone else too ;)

---

### Post by Amadeus793 on 2010-03-22
> **cagney said:**
> If you are on Ubuntu 9.10, and have gpsd installed, all you have to do to get gps going is to plug in the gps connection, provided you have the following set in OpenCPN:
ToolBox => GPS => NMEA DAta Source == Network GPSD

The instructions you are following, was a workaround when gpsd did not start automatically. This is now fixed.

I have a Garmin GPSmap 60CSx and can safely say that GPSD does not auto detect my GPS. I have tried to find a solution for weeks now. But the old workaround with old kernel is the only solution that work. I have tried the same on three computers using Ubuntu 9.10.

---

### Post by emptybottle on 2010-03-22
To Cagney: 

My Garmin GPS is not autodetected by GPSD and yes the service is started. I can see my GPS when use lsusb command. If I use your method xgps says it can't find any GPS

---

