---
title: "War Driving"
date: 2012-01-24
forum: General Help
---

### Post by soccer05 on 2012-01-24
I am currently attempting to connect my bluetooth GPS device to my linux machine and use gpsd with it.
 
Now when I try to execute gpsd using:
```
 gpsd -N -n -D 3 /dev/rfcomm0 
```
 
I get the following output, followed by a stall:
```
gpsd: launching (Version 2.38)
gpsd: listening on port gpsd
gpsd: Priority sertting failed.
gpsd: shmat(983059,0,0) succeeded
gpsd: shmat(1015828,0,0) succeeded
gpsd: shmat(1048597,0,0) succeeded
gpsd: shmat(1081366,0,0) succeeded
gpsd: successfully connected to the DBUS system bus
gpsd: running with effective group ID 0
gpsd: running with effective user ID 0
gpsd: opening GPS data source at '/dev/rfcomm0'
gpsd: speed 9600, 8N1
```
 
Can anyone please assist me with this issue?
Thanks.

---

### Post by Mark Phelps on 2012-01-24
You mentioned War Driving in the title ... a term often confused with "piggybacking" these days.

The former term means to search for open WiFi networks while driving around in a vehicle -- quite legal, and easily done.

The latter refers to using the former to obtain closed WiFi network info and then "hacking" into the networks without authorization.  This activity is illegal in many areas.

Just mentioning this so you know the difference -- as the media, never interested in the technical correctness of what they report -- often use the terms interchangeably.

---

### Post by soccer05 on 2012-01-24
Yes, I am not referering to anything illegal. I just want to see what kind of networks are around my house.

---

