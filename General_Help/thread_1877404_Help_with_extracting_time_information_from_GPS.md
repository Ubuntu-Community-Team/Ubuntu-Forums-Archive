---
title: "Help with extracting time information from GPS"
date: 2011-11-08
forum: General Help
---

### Post by jmcoreymv on 2011-11-08
Hi,

I just purchased a USB GPS device looking to extract time information from GPSD and pass it to NTPD to get an accurate system clock.  I'm using Ubuntu 10.04 LTS.

I believe the GPS is working because I can run xgps and see the satellites/time info/location/etc.

However I can't quite figure out how to get ntpd to pull the information from gpsd.  I've modified my /etc/ntp.conf to:

```

server 127.127.28.0 minpoll 4 maxpoll 4
fudge 127.127.28.0 refid GPS

restrict 127.0.0.1
restrict 10.1.1.0 mask 255.255.255.0 nomodify notrap


```

where 127.127.28.0 is supposed to be the IP to access the GPS information.  I can ping that IP successfully.  However when I try to access the server using ntpq -p, it says 'No association ID's returned'.

If I stop NTPD and run 'ntpdate 127.127.28.0' it says there were no suitable synchronization servers found. 

NTPD works fine if I point it to a public time server.  

Any help is greatly appreciated!

Thanks

---

### Post by jeffme on 2011-11-08
friendly bump... I'm curious, too....

---

### Post by jmcoreymv on 2011-11-08
I was able to get the ntpd <-> gps link working last night with some help from a gpsd mailing list.  I had to compile ntpd from scratch so it would include the SHM (shared memory) drive to access the GPSD time.  

The issue I'm seeing now is that the GPS reported time is ~24 seconds ahead of UTC.  I did some quick googling and saw that Loran-C time is 24 seconds ahead of UTC.  I'm not sure how to get NTP/GPS to switch time systems if that's really whats going on.  Any ideas?

Thanks!

---

