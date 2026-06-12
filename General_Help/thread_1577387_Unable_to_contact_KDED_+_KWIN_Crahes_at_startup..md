---
title: "Unable to contact KDED + KWIN Crahes at startup."
date: 2010-09-18
forum: General Help
---

### Post by popppppz on 2010-09-18
Kubuntu Maverick Meerkat 10.10 says "Unable to contact KDED". This in return diables all of my KDE services. I have already freshly installed 10.10 2 times. Also when I first login it says KWIN has crashed, but I see it running in the service Manager. Please help, I have no internet service without KDE services. :(

---

### Post by Zorael on 2010-09-19
Have a look at **/var/log/kdm.log**; does it say anything of interest? Perhaps why kded crashed?



**edit:** I got this on my maverick machine this morning. For me it was a case of something broken in the packages, so I just had to upgrade them.

Since I couldn't connect to my wireless network without kded's network management module running, I used a network cable instead, plugging it directly into my router. From a console I then updated packages.
```
$ sudo dhclient eth0   # requires DHCP enabled in router
$ sudo aptitude update
$ sudo aptitude full-upgrade
$ sync
$ sudo restart kdm
```

---

### Post by popppppz on 2010-09-23
yeah i couldnt fine any reason for the crash, i ended up reinstalling 10.04 thanks though

---

