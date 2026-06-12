---
title: "GPS Question"
date: 2006-03-08
forum: General Help
---

### Post by seekyrr on 2006-03-08
Looking for a GPS to work with breezy 5.10.  I would like to configure it with Kismet.

Anyone recomend a cheaper GPS unit which would be compatible with Breezy 5.10?

Thanks

Seek

---

### Post by prizrak on 2006-03-08
I would suggest checking Garmin to see what they have an what OS's they would work with. GPS is a tricky beast it's a bit too specific of hardware to be easily supported.

---

### Post by allanj on 2006-04-12
Well I just bought the cheapest USB GPS reciever I could find the Haicom HI-204E - USB, and it works perfectly under debian sarge with gpsdrive, but under kubuntu there are problems, the dbus thing interferes with the GPS signals coming in through serial-usb, so gpsdrive can not see the reciever.
If anyone knows how to fix that it would be great.

Best regards
Allan Jacobsen

---

### Post by fattmox on 2006-04-13
I too am having problems with my GPS mouse running over USB-Serial. 

8826: arguments to dbus_message_iter_append_basic() were incorrect, assertion "real->iter_type == DBUS_MESSAGE_ITER_TYPE_WRITER" failed in file dbus-message.c line 2125.

I am running a Holux GM 210 USB Mouse GPS with Ubuntu 5.10 Breezy Badger. Has there been any progress with this issue?

---

### Post by int on 2006-04-13
when I connected my usb gps show: (dmeg)

> 4316160.497000] usb 1-1: new full speed USB device using uhci_hcd and address 5[4316160.626000] pl2303 1-1:1.0: pl2303 converter detected
[4316160.626000] usb 1-1: pl2303 converter now attached to ttyUSB0
install this:
```
sudo apt-get install gpsd gpsd-clients gpsdrive
```

Connect GPS USB to computer.
```
sudo killall gpsd
sudo mknod /dev/ttyUSB0 c 188 0
sudo gpsd -N -n -D 2 /dev/ttyUSB0 &
gpsdrive
```

in Preference */dev/ttyUSB0*

---

### Post by murder2 on 2006-09-20
I am exoeriencing similar "problems" with my GlobalSat BU-353 under Dapper.

```

$ gpsd -N -n -D 2 /dev/ttyUSB0
gpsd: launching (Version 2.30)
gpsd: listening on port gpsd
gpsd: successfully connected to the DBUS system bus
gpsd: running with effective group ID 1000
gpsd: running with effective user ID 1000
gpsd: opening GPS data source at '/dev/ttyUSB0'
gpsd: speed 9600, 8N1
gpsd: gpsd_activate: opened GPS (5)
gpsd: => GPS: $PFEC,GPint,GSA01,DTM00,ZDA01,RMC01,GLL00,VTG00,GSV05*3B\x0d

gpsd: => GPS: @NC10151010\x0d

gpsd: => GPS: $PMOTG,ZDA,1*2F\x0d

gpsd: => GPS: $PGRMCE*0E\x0d

gpsd: => GPS: $PSRF105,1*3E\x0d

gpsd: => GPS: $PFST*11\x0d

gpsd: <= GPS: $GPGGA,124729.000,5809.8524,N,00800.1920,E,1,04,2.9,25.5,M,42.2,M,,0000*63
gpsd: can't use GGA/GGL time until after ZDA or RMC has supplied a year.
17569: arguments to dbus_message_iter_append_basic() were incorrect, assertion "real->iter_type == DBUS_MESSAGE_ITER_TYPE_WRITER" failed in file dbus-message.c line 2125.
This is normally a bug in some application using the D-BUS library.
```
Then the "17596: arguments..." part just keeps repeating until I terminate gpsd:
```

gpsd: <= GPS: $GPVTG,340.46,T,,M,1.11,N,2.1,K*67
gpsd: closing GPS=/dev/ttyUSB0 (5)
gpsd: Received terminating signal 2. Exiting...

```

However, when running gpsdrive, it does find my location, and it seems to be working, it's reciving data from the gps device. So, am I really having a problem here? :confused:  

Any thoughts?

---

