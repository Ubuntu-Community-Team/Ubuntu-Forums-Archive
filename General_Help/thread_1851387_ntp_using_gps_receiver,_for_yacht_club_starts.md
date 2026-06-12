---
title: "ntp using gps receiver, for yacht club starts"
date: 2011-09-28
forum: General Help
---

### Post by Reduced_Oxygen on 2011-09-28
I work at a yacht club and we recently stated using a gps receiver to obtain an accurate time for starts and finishes. the system thats going atm is on windows (face palm)and can only update every minute. so heres my question can u do better? and is there a nice large clock i can use with it (for the old people 2 see)

i was hoping for updates at once a second.


let me know

---

### Post by Reduced_Oxygen on 2011-09-30
OMG! bump -_-

---

### Post by Reduced_Oxygen on 2011-10-03
really at least a tutorial on using a gps to receive the time would be nice. BUMP!

---

### Post by Reduced_Oxygen on 2011-10-21
bump

---

### Post by jeffme on 2011-11-08
Hi - check out these pages:

[http://www.rjsystems.nl/en/2100-ntpd-garmin-gps-18-lvc-gpsd.php](http://www.rjsystems.nl/en/2100-ntpd-garmin-gps-18-lvc-gpsd.php)
[http://manpages.ubuntu.com/manpages/dapper/man8/gpsd.8.html](http://manpages.ubuntu.com/manpages/dapper/man8/gpsd.8.html)

Unfortunately, I haven't been able to get it to work totally properly (I'm not seeing any info in when/reach/delay/offset/jitter on the ntpq -p output) but you should be able to read your GPS data on the laptop fairly easily.

---

### Post by rafeladruson on 2012-08-24
I had gone through the post. The information which are provided about the gps receive such as gps can use differential-GPS corrections from a DGPS radio or over the net, from a ground station running a DGPSIP server that reports RTCM-S104 data. Please produce some more attachments about the topic for view detail information.

[yacht charter](http://www.navis-yacht-charter.com/) 
[luxury yacht charter](http://www.navis-yacht-charter.com/)

---

### Post by Cheesehead on 2012-08-24
Yes, you can use gps receivers to update NTP.
Yes, you can use a screen to display the time (or clock) in big numbers.

The first step is to install the "gpsd" package onto your system. gpsd is the daemon that listens for gps signals from hardware, and outputs useful location/time data for other processes like navigators or NTP to use. See if gpsd can read the time from your hardware. The gpsd package includes several test programs like xgps for precisely that purpose.

The second step is to look at time displays. I suggest the "dclock" package, which is simple, very customizable, and easily resizable to fill the whole screen. Check out the dclock man page. If you want to use different external hardware, see if it's compatible with your system.

The final step is to edit your /etc/ntp.conf to use gpsd time output as a valid ntp input. One example of how to do that is in step 5 of [http://www.rjsystems.nl/en/2100-ntpd-garmin-gps-18-lvc-gpsd.php](http://www.rjsystems.nl/en/2100-ntpd-garmin-gps-18-lvc-gpsd.php)

Let us know what you need more detail or help with!

---

