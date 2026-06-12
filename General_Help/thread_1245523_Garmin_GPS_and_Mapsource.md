---
title: "Garmin GPS and Mapsource"
date: 2009-08-20
forum: General Help
---

### Post by jfl on 2009-08-20
I am (slowly) getting to the point I will be able to finally remove Windoze from this laptop; it ha sbeen months since I dual booted W2K.

My last obstacle is one of my Garmin GPS.
I run Mapsource under Wine, works OK, causes system crashes from time to time.
I did the code thingy:
```
sudo modprobe garmin_gps
dmesg
sudo ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com1

```
Commented out garmin in the blacklist.
Everything works well with my Quest 2.

However with the Garmin GPSMAP 376C, I hit a snag.
Mapsource find the 376 with no problem; when I try to upload/dowload waypoints, routes, the transfer starts, then aborts with a pop-up saying there is no device connected ???
If I reconnect the Quest2, it works fine again  :confused:
Spent the afternoon on the web with no success.

Running Jaunty for 4 days now.

---

### Post by Zill on 2009-08-20
jfl:  Garmin are not "Linux friendly" at the moment. :-(

I can only suggest that you email Garmin to add your complaint to others in the hope that they will eventually see that it makes commercial sense for them to support the, ever increasing, numbers of Linux users.

In the meantime, if anyone knows of any Linux friendly GPS/Satnav manufacturers then please advise so we can all vote with our cash!

---

### Post by TheropodWatcher on 2009-08-23
I have found that Viking (available through the repository) and a USB to Serial adapter work fine for downloading the waypoints and trackpoints. You can overlay them on various maps available through the program, though you can't get at the hugely proprietory Garmin maps. Looks like this is going to work for me. I'm using a Rino 120,
 Ummmm ... what's this blacklist you talk about? Sounds interesting.
 Brad

---

### Post by phyrewall on 2010-08-15
> **TheropodWatcher said:**
> I have found that Viking (available through the repository) and a USB to Serial adapter work fine for downloading the waypoints and trackpoints. You can overlay them on various maps available through the program, though you can't get at the hugely proprietory Garmin maps. Looks like this is going to work for me. I'm using a Rino 120,
 Ummmm ... what's this blacklist you talk about? Sounds interesting.
 Brad

/etc/modprobe.d/blacklist.conf contains the following lines related to this issue:
```
# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

```

I'm assuming he commented that one out. Hope this helps.

---

