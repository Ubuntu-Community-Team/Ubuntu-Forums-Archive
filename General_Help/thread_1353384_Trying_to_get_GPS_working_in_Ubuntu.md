---
title: "Trying to get GPS working in Ubuntu"
date: 2009-12-12
forum: General Help
---

### Post by checkm8 on 2009-12-12
I have a Holux M1000 Gps receiver that I am trying to get working in ubuntu with a USB connection (The Holux M1000 supports bluetooth and I am unsure of usb ability). If this gps receiver does not support USB then I have another gps device that I use in my car, a Garmin nuvi 205. 

Will any of these help me find wireless networks with a gps device? I am trying to find wireless networks in my area with GPS and am unable to establish a proper connection via usb to my GPS device. 

Can anyone help?

---

### Post by efflandt on 2009-12-12
Garmin Nuvi's do not output current position, even with Garmin software.  The USB is just for charging and/or updating maps, adding POI's, etc. (and images and mp3 files for units capable of that).  My Nuvi 750 does tracking, but that only shows where you have been, not necessarily where you are.

Their handhelds and other non-automotive models do output current position.  I have a circa 1995 serial Garmin GPS 45, eTrex Legend HCx USB, and GPS 10x Bluetooth (to use with my Palm TX).  But I have not tried them in Linux yet.

---

### Post by checkm8 on 2009-12-12
If Garmins do not output their GPS coordinates via usb, how about my Holux? I am curious to know how to get this GPS to register in ubuntu and update a software of the wireless router position.

---

### Post by BrownieMan on 2010-01-16
> **checkm8 said:**
> If Garmins do not output their GPS coordinates via usb, how about my Holux? I am curious to know how to get this GPS to register in ubuntu and update a software of the wireless router position.

this might give you some insight. I'm in teh exact same siutaiton as you with a Holux M-1000. I can't get it to work... YET

---

### Post by macca61 on 2010-03-04
> **checkm8 said:**
> If Garmins do not output their GPS coordinates via usb, how about my Holux? I am curious to know how to get this GPS to register in ubuntu and update a software of the wireless router position.
 
Although I can't help at all on the Ubuntu side, the Holux does provide coordintes via the USB in several different formats  [http://www.holux.com/JCore/en/products/products_spec.jsp?pno=222](http://www.holux.com/JCore/en/products/products_spec.jsp?pno=222)

---

### Post by jcoli on 2010-08-22
anyone can get to connect the Holux M1000 into Ubuntu?

---

### Post by surfer on 2010-08-22
i have a holux gpsport 245 and tried that (without success) so far:

```


# apt-get install mtkbabel

$ mtkbabel

$ mtkbabel -s 38400

$ gpsbabel -t -i m245 -f /dev/ttyUSB0 -o gpx -F track.gpx


```

---

### Post by surfer on 2010-09-12
i seem to be able to read things from my device by now. but there seem to be errors in the data, so nothing useful yet.
```

$ **mtkbabel -s 38400 -l off -f foo -w -t**
MTK Test OK
MTK Firmware: Version: 1, Release: M-core_2.12, Model ID: 0000
>> Switch recording to OFF
Log format: (8800003D) UTC,LATITUDE,LONGITUDE,HEIGHT,SPEED
Size in bytes of each log record: 30 + (0 * sats_in_view)
Logging TIME interval:       5.00 s
Logging DISTANCE interval:   0.00 m
Logging SPEED limit:         0.00 km/h
Recording method on memory full: (1) OVERLAP
Log status: (000100000000) AUTOLOG_OFF,OVERLAP_WHEN_FULL,ENABLE_LOG
Next write address: 164444 (0x0002825C)
Number of records: 8002
Memory health status (failed sectors mask): FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF
>> Retrieving 2097152 (0x00200000) bytes of log data from device...
Saved log data:   0.00%
.....
Saved log data:   9.28%
WARNING: Sector header at offset 0x00030000 is non-written data
Saved log data:   9.38%
ERROR: Checksum separator error: expected char 0x2A, found 0xCB

```

and

```

$ **gpsbabel -v -t -i holux -f /dev/ttyUSB0 -o gpx -F track.gpx**
holux: Invalid latitude 14505.096000 in waypoint .

```

has someone got any of this to really work?

---

### Post by savantelite on 2010-10-25
Bump, I have a holux 1200 that am I still trying to connect.

---

