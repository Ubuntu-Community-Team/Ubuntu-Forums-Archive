---
title: "serial connection to Garmin Etrex"
date: 2011-01-01
forum: General Help
---

### Post by Sundowner on 2011-01-01
I have the 10.4 netbook remix and I have checked everything on the forum for connecting to may Garmin Etrex hand held gps but all possible solutions have failed.
the GPS connects via a usb/serial converter and all I want to do is download recent tracks from the gps and upload new routes and waypoints.
If I can do this I can get rid of Windows.

I'd appreciate any help you could give me.

When the GPS is attached a device ttyUSB0 is created in /dev.
I then use gpsbabel with the following result.
 
$ sudo gpsbabel -t -i garmin -f ttyUSB0: -o gpx -F /GPS/GarminTracks.gpx
[ERROR] XSERIAL: Cannot open serial port 'ttyUSB0:': No such file or directory
[ERROR] Cannot open serial port 'ttyUSB0:'
GARMIN:Can't init ttyUSB0:

 I have tried creating the file /etc/udev/rules/51-garmin.rules as suggested elsewhere without success.


has anyone ever managed to get this to work?

---

