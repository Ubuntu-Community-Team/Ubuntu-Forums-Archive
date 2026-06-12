---
title: "Cups problem"
date: 2006-02-18
forum: General Help
---

### Post by php on 2006-02-18
OK, so now I'm getting so tired of my printing problems so I actually start a thread =)

I experience some strange problems with printing. I have a printer connected to my Netgear FM114P router. I have configured CUPS to use this as a network printer over lpr. Lately I've get strange lockups and it's not possible to print.

It seems like CUPS aren't really up and working. If I (in GNOME) choose System->Admin->Printing I only get an error pop-up saying "The CUPS server could not be contacted". The cupsd is up and running:

> ps aux| grep cup
root     12794  0.0  0.2   6636  1492 ?        Ss   11:00   0:00 /usr/sbin/cupsd -F
root     12809  0.0  0.1   3428   776 ?        D    11:00   0:00 /usr/lib/cups/backend/epson

If I try /etc/init.d/cupsys restart i get another "epson" process and the cupsd process restarts. The old "epson" processes can't be killed, not even with force.

/var/log/cups/error_log only contains a lot of entries like this:

I [18/Feb/2006:09:07:26 +0100] Listening to 7f000001:631
I [18/Feb/2006:09:07:26 +0100] Loaded configuration file "/etc/cups/cupsd.conf"
I [18/Feb/2006:09:07:26 +0100] Configured for up to 100 clients.
I [18/Feb/2006:09:07:26 +0100] Allowing up to 100 client connections per host.
I [18/Feb/2006:09:07:26 +0100] Full reload is required.
W [18/Feb/2006:09:07:56 +0100] LoadDevices: Backend did not respond within 30 se

Strangely, sometimes after a /etc/init.d/cupsys restart I get other entries like this:

I [18/Feb/2006:11:31:47 +0100] Listening to 7f000001:631
D [18/Feb/2006:11:31:47 +0100] AddLocation: added location '/'
D [18/Feb/2006:11:31:47 +0100] DenyIP: / deny 00000000/00000000
D [18/Feb/2006:11:31:47 +0100] AllowIP: / allow 7f000001/ffffffff
D [18/Feb/2006:11:31:47 +0100] AddLocation: added location '/jobs'
D [18/Feb/2006:11:31:47 +0100] AddLocation: added location '/admin'
D [18/Feb/2006:11:31:47 +0100] DenyIP: /admin deny 00000000/00000000
D [18/Feb/2006:11:31:47 +0100] AllowIP: /admin allow 7f000001/ffffffff
I [18/Feb/2006:11:31:47 +0100] Loaded configuration file "/etc/cups/cupsd.conf"
I [18/Feb/2006:11:31:47 +0100] Configured for up to 100 clients.
I [18/Feb/2006:11:31:47 +0100] Allowing up to 100 client connections per host.
I [18/Feb/2006:11:31:47 +0100] Full reload is required.
D [18/Feb/2006:11:31:47 +0100] LoadAllPrinters: Loading printer Okipage 8p...
d [18/Feb/2006:11:31:47 +0100] AddPrinter("Okipage 8p")
d [18/Feb/2006:11:31:47 +0100] Adding filter application/vnd.cups-raw printer/Okipage 8p 0 -
d [18/Feb/2006:11:31:47 +0100] FindBest: uri = "/printers/Okipage 8p"...
d [18/Feb/2006:11:31:47 +0100] FindBest: Location / Limit 7f
d [18/Feb/2006:11:31:47 +0100] FindBest: Location /jobs Limit 7f
d [18/Feb/2006:11:31:47 +0100] FindBest: Location /admin Limit 7f
d [18/Feb/2006:11:31:47 +0100] FindBest: best = "/"
d [18/Feb/2006:11:31:47 +0100] Adding filter application/vnd.cups-postscript printer/Okipage 8p 0 foomatic-rip
D [18/Feb/2006:11:31:47 +0100] LoadDevices: Added device "ipp"...
D [18/Feb/2006:11:31:47 +0100] LoadDevices: Added device "http"...
D [18/Feb/2006:11:31:47 +0100] LoadDevices: Added device "bluetooth"...
D [18/Feb/2006:11:31:47 +0100] LoadDevices: Added device "hp:/no_device_found"...
D [18/Feb/2006:11:31:47 +0100] LoadDevices: Added device "smb"...
D [18/Feb/2006:11:31:47 +0100] LoadDevices: Added device "lpd"...
D [18/Feb/2006:11:31:47 +0100] LoadDevices: Added device "parallel:/dev/lp0"...
D [18/Feb/2006:11:31:47 +0100] LoadDevices: Added device "socket"...
D [18/Feb/2006:11:31:47 +0100] LoadDevices: Added device "usb:/dev/usb/lp0"...
D [18/Feb/2006:11:31:47 +0100] LoadDevices: Added device "usb:/dev/usb/lp1"...
D [18/Feb/2006:11:31:47 +0100] LoadDevices: Added device "usb:/dev/usb/lp2"...
D [18/Feb/2006:11:31:47 +0100] LoadDevices: Added device "usb:/dev/usb/lp3"...
D [18/Feb/2006:11:31:47 +0100] LoadDevices: Added device "usb:/dev/usb/lp4"...
D [18/Feb/2006:11:31:47 +0100] LoadDevices: Added device "usb:/dev/usb/lp5"...
D [18/Feb/2006:11:31:47 +0100] LoadDevices: Added device "usb:/dev/usb/lp6"...
D [18/Feb/2006:11:31:47 +0100] LoadDevices: Added device "usb:/dev/usb/lp7"...
D [18/Feb/2006:11:31:47 +0100] LoadDevices: Added device "usb:/dev/usb/lp8"...
D [18/Feb/2006:11:31:47 +0100] LoadDevices: Added device "usb:/dev/usb/lp9"...
D [18/Feb/2006:11:31:47 +0100] LoadDevices: Added device "usb:/dev/usb/lp10"...
D [18/Feb/2006:11:31:47 +0100] LoadDevices: Added device "usb:/dev/usb/lp11"...
D [18/Feb/2006:11:31:47 +0100] LoadDevices: Added device "usb:/dev/usb/lp12"...
D [18/Feb/2006:11:31:47 +0100] LoadDevices: Added device "usb:/dev/usb/lp13"...
D [18/Feb/2006:11:31:47 +0100] LoadDevices: Added device "usb:/dev/usb/lp14"...
D [18/Feb/2006:11:31:47 +0100] LoadDevices: Added device "usb:/dev/usb/lp15"...
W [18/Feb/2006:11:32:17 +0100] LoadDevices: Backend did not respond within 30 seconds!

Am I doing something wrong or is CUPS really messed up?

Best regards,

PH

---

### Post by arvelius on 2006-05-07
I've got exactly the same problem. Did you find a solution? 

Got my new printer (samsung ML-2010) to work locally (with the ML-4500 driver) a week ago, with some struggeling in config files over the network a couple of days ago, printed without problems yesterday and today nothing. The computer and the printer has been on the whole time and I  have had no activities that I can relate to the printer or cups inbetween. After reading your message I realised I have several "epson processes" also: 

$ ps aux| grep cup
johan    14726  0.0  0.8 129616  4260 ?        Ss   May01   0:51 gnome-cups-icon --sm-config-prefix /gnome-cups-icon-HmPnKK/ --sm-client-id 1044f54bda000113482755200000030960005 --screen 0
root     13335  0.0  2.6 155132 13572 pts/7    Sl   May02   0:53 gedit cupsd.conf
johan    19877  0.0  1.9 143120  9800 ?        S    May04   0:38 gnome-cups-manager
root     20609  0.0  0.1  17336   704 ?        DN   07:35   0:00 /usr/lib/cups/backend/epson
root      6949  0.0  0.1  17340   952 ?        D    15:24   0:00 /usr/lib/cups/backend/epson
root     13271  0.0  0.1  17340   952 ?        D    18:10   0:00 /usr/lib/cups/backend/epson
root     13404  0.0  0.1  17340   948 ?        D    18:13   0:00 /usr/lib/cups/backend/epson
root     13898  0.0  0.3  26692  1852 ?        Ss   18:26   0:00 /usr/sbin/cupsd -F
root     13904  0.0  0.1  17336   948 ?        D    18:26   0:00 /usr/lib/cups/backend/epson
johan    15482  0.0  0.1   6036   884 pts/5    S+   19:01   0:00 grep cup
$

ofcourse after a some restarts of cupsys when I realized it was dead. They cannot be killed.

My logfile is very similar to the previous, from the last restart I got the following contribution:

I [07/May/2006:18:26:20 +0200] Listening to 0:631
D [07/May/2006:18:26:20 +0200] AddLocation: added location '/'
D [07/May/2006:18:26:20 +0200] DenyIP: / deny 00000000/00000000
D [07/May/2006:18:26:20 +0200] AllowIP: / allow 00000000/00000000
D [07/May/2006:18:26:20 +0200] AddLocation: added location '/jobs'
D [07/May/2006:18:26:20 +0200] AddLocation: added location '/admin'
D [07/May/2006:18:26:20 +0200] DenyIP: /admin deny 00000000/00000000
D [07/May/2006:18:26:20 +0200] AllowIP: /admin allow 7f000001/ffffffff
I [07/May/2006:18:26:20 +0200] Loaded configuration file "/etc/cups/cupsd.conf"
I [07/May/2006:18:26:20 +0200] Configured for up to 100 clients.
I [07/May/2006:18:26:20 +0200] Allowing up to 100 client connections per host.
I [07/May/2006:18:26:20 +0200] Full reload is required.
D [07/May/2006:18:26:20 +0200] LoadAllPrinters: Loading printer ML-4500...
E [07/May/2006:18:26:20 +0200] LoadAllClasses: Unable to open /etc/cups/classes.conf - Filen eller katalogen finns inte
D [07/May/2006:18:26:21 +0200] LoadDevices: Added device "smb"...
D [07/May/2006:18:26:21 +0200] LoadDevices: Added device "ipp"...
D [07/May/2006:18:26:21 +0200] LoadDevices: Added device "bluetooth"...
W [07/May/2006:18:26:51 +0200] LoadDevices: Backend did not respond within 30 seconds!

---

### Post by php on 2006-05-07
No, I haven't found any solutions, but the problem hasn't occoured for a while now ;(

---

### Post by arvelius on 2006-05-07
What do you mean hasn't occured? How did you get it printing again? Did you get rid of the strange processes?

---

### Post by arvelius on 2006-05-08
Thought this might be du to a malfunctional epson driver but when I removed it I got an /usr/lib/cups/backend/canon process instead that wasn't possible to kill either. Gave up in the end and rebooted the whole system and then the printer was working again. To me this seems buggy but I've been fiddeling around in the config files maybe too much. Is there someone who has this problem right out of the box?

---

