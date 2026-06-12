---
title: "isdnlog doesn't start my script on ring"
date: 2010-12-03
forum: General Help
---

### Post by Lorem on 2010-12-03
I have a Fritz!Card PCI which I used to display and log calls to my phone on Windows XP with.
Now that I use Ubuntu Maverick x64, I tried to do the same with isdnlog.
Logging the calls to /var/lib/isdn/calls works fine, but the START command doesn't work.

I have experimented with different parameters (user, group, interval, time, flags) in the start section, nothing worked.

I have read [this tutorial]("http://www.staschke.de/linux/anwahl.html") to get started.
The installed version of isdnlog is 1:3.12.20071127-0ubuntu6.

Here you see the files:

/etc/isdn/isdnlog.isdnctrl0
```
# This is a very short summary with the important options.
# for a longer descriptions of all options : please read isdnlog(8)


[options]

#log=1         # log d-channel messages. value may be 0-15 (bit coded flags)
daemon=yes    # "yes"/"no": (dont) start isdnlog as daemon. Set yes for Debian
stdout=0x3f7    # log to stdout and file, and set log level
 # if you remove "outfile" option, also remove "stdout" option!
outfile=+/var/log/isdn/isdnlog    # logfile to log to ('+' is append mode)
console=/dev/null    # where to send stdout text; e.g. /dev/tty12
#monitor=yes    # enable support for imon and imontty (monitor progs)
syslog=0x1bf7    # log to syslog with log level X
#thruput=60    # if you log thruput : one message every X seconds
#time=2        # 1=get time from isdn one, 2=everytime 
#hangup=5:3    # enable chargehup with 5 / 3 seconds security gap
**start=yes**    # enable program start on events
ciInterval=59   # show the cost etc. every 60s
#internS0=3

# If you have the Deutsche Telekom cityweekend thing,
# enable the cityweekend option in isdn.conf.
```/etc/isdn/isdn.conf
```
# example of /etc/isdn/isdn.conf
#
# More information: /usr/doc/packages/i4l/isdnlog/*


[GLOBAL]
COUNTRYPREFIX   = +
COUNTRYCODE     = 49
AREAPREFIX      = 0

# EDIT THIS LINE:
AREACODE        =  *XXXX #my areacode without preceding 0*

[VARIABLES]

[ISDNLOG]
LOGFILE = /var/lib/isdn/calls
ILABEL  = %b %e %T %ICall to tei %t from %N2 on %n2
OLABEL  = %b %e %T %Itei %t calling %N2 with %n2
REPFMTWWW       = "%X %D %17.17H %T %-17.17F %-20.20l SI: %S %9u %U %I %O"
REPFMTSHORT     = "%X%D %8.8H %T %-14.14F%U%I %O"
REPFMTNIO       = "  %X %D %16.16H %T %-25.25F %U"
REPFMT  = "  %X %D %16.16H %T %-16.16F %7u %U %I %O"
CHARGEMAX       = 50.00
CURRENCY = 0.062,EUR

START = {
[FLAG]
FLAGS = IRU
PROGRAM = /usr/bin/notify_isdn
INTERVAL = 2
}

COUNTRYFILE = /usr/share/isdn/country.dat
RATECONF= /etc/isdn/rate.conf
RATEFILE= /usr/share/isdn/rate-de.dat
HOLIDAYS= /usr/share/isdn/holiday-de.dat
ZONEFILE= /usr/share/isdn/zone-de-%s.cdb
DESTFILE= /usr/share/isdn/dest.cdb

# providerselect
VBN = 010:01900:09005
VBNLEN = 2:3
PRESELECTED=33
```/etc/isdn/callerid.conf```
[MSN]
NUMBER=16
SI=1
ALIAS=PC
START = {
    [FLAG]
    FLAGS=IRU
    USER=*{my username}*
    GROUP=users
    INTERVAL=5
    PROGRAM=/usr/bin/notify_isdn
}

[MSN]
NUMBER=15
SI=1
ALIAS=Privat
START = {
    [FLAG]
    FLAGS=IRU
    USER=*{my username}*
    GROUP=users
    INTERVAL=5
    PROGRAM=/usr/bin/notify_isdn
}
```The numbers are internal msns.

/usr/bin/notify_isdn
```
#!/bin/bash
notify-send "Test" "test"
```When I run the script, the notification pops up.

When I restart isdnlog, it says:
```
$ sudo service isdnutils restart
 * Restarting ISDN services:
 *   There is apparently no configuration created yet.
 *   You can create configuration files with the 'isdnconfig' tool.
 *  
 *   If you don't want this warning in future, please create the file
 *      /etc/isdn/noconfig
 *   For more information, see /usr/share/doc/isdnutils-base/HOWTO.isdnutils.gz

                        [ OK ]

```After restarting, I have called the PC from the phone (internal call).
/var/log/isdn/isdnlog:
```

isdnlog Version 4.71 starting
Holiday Version 1.10-Germany [12-Apr-1999] loaded [11 entries from /usr/share/isdn/holiday-de.dat]
Dest V1.01: File '/usr/share/isdn/dest.cdb' opened fine - Dest 1.0 int (+h) AT DE NL CH BE
Zone V1.25: Provider 0 File '/usr/share/isdn/zone-de-dtag.cdb' opened fine - V1.25 K2 C2 N256 T157147 O1 L5
Rates   Version 3.12 [27-Feb-2005 22:15:34] loaded [87 Providers, 0 skipped, 1325 Zones, 4755 Areas, 86 Services, 726 Comments, 10 eXceptions, 65 Redirects, 4298 Rates from /usr/share/isdn/rate-de.dat]
(ISDN subsystem with ISDN_MAX_CHANNELS > 16 detected, ioctl(IIOCNETGPN) is available)
isdn.conf:2 active channels, 2 MSN/SI entries
(Data versions: iprofd=0x06  net_cfg=0x06  /dev/isdninfo=0x01)
Everything is fine, isdnlog-4.71 is running in full featured mode.
(AVM B1 driver detected (D2))
Dec 03 11:46:31 * Call to tei 127 from TN **15 on PC  RING (Speech)
Dec 03 11:46:31 * Call to tei 127 from TN **15 on PC  HLC: CCITT, Telefonie
Dec 03 11:46:35 tei 93 calling ? with ?  HANGUP

```/var/log/syslog
```

Dec  3 11:46:29 pc isdnlog: isdnlog Version 4.71 starting
Dec  3 11:46:29 pc isdnlog: Holiday Version 1.10-Germany [12-Apr-1999] loaded [11 entries from /usr/share/isdn/holiday-de.dat]
Dec  3 11:46:29 pc isdnlog: Dest V1.01: File '/usr/share/isdn/dest.cdb' opened fine - Dest 1.0 int (+h) AT DE NL CH BE
Dec  3 11:46:29 pc isdnlog: Zone V1.25: Provider 0 File '/usr/share/isdn/zone-de-dtag.cdb' opened fine - V1.25 K2 C2 N256 T157147 O1 L5
Dec  3 11:46:29 pc isdnlog: Rates   Version 3.12 [27-Feb-2005 22:15:34] loaded [87 Providers, 0 skipped, 1325 Zones, 4755 Areas, 86 Services, 726 Comments, 10 eXceptions, 65 Redirects, 4298 Rates from /usr/share/isdn/rate-de.dat]
Dec  3 11:46:29 pc isdnlog: (ISDN subsystem with ISDN_MAX_CHANNELS > 16 detected, ioctl(IIOCNETGPN) is available)
Dec  3 11:46:29 pc isdnlog: isdn.conf:2 active channels, 2 MSN/SI entries
Dec  3 11:46:29 pc isdnlog: (Data versions: iprofd=0x06  net_cfg=0x06  /dev/isdninfo=0x01)
Dec  3 11:46:29 pc isdnlog: Everything is fine, isdnlog-4.71 is running in full featured mode.
Dec  3 11:46:30 pc isdnlog: (AVM B1 driver detected (D2))
Dec  3 11:46:31 pc isdnlog: Dec 03 11:46:31 * tei 93 calling ? with ?  CHANNEL: BRI, B1 needed
Dec  3 11:46:31 pc isdnlog: Dec 03 11:46:31 * tei 93 calling ? with ?  PROGRESS: Private network serving local user
Dec  3 11:46:31 pc isdnlog: Dec 03 11:46:31 * tei 93 calling ? with ?  PROGRESS: inband information available
Dec  3 11:46:31 pc isdnlog: Dec 03 11:46:31 * Call to tei 127 from ? on ?  BEARER: Speech, CCITT standardized coding
Dec  3 11:46:31 pc isdnlog: Dec 03 11:46:31 * Call to tei 127 from ? on ?  64 kbit/s, Circuit mode
Dec  3 11:46:31 pc isdnlog: Dec 03 11:46:31 * Call to tei 127 from ? on ?  G.711 A-law
Dec  3 11:46:31 pc isdnlog: Dec 03 11:46:31 * Call to tei 127 from ? on ?  CHANNEL: BRI, B2 needed
Dec  3 11:46:31 pc isdnlog: Dec 03 11:46:31 * Call to tei 127 from TN **15 on PC  RING (Speech)
Dec  3 11:46:31 pc isdnlog: Dec 03 11:46:31 * Call to tei 127 from TN **15 on PC  HLC: CCITT, Telefonie
Dec  3 11:46:31 pc kernel: [ 9477.745533] capidrv-1: incoming call **15,1,1,16
Dec  3 11:46:31 pc kernel: [ 9477.745541] capidrv-1: patching si2=1 to 0 for VBOX
Dec  3 11:46:31 pc kernel: [ 9477.745548] isdn_net: call from **15 -> 0 16 ignored
Dec  3 11:46:31 pc kernel: [ 9477.745557] isdn_tty: call from **15 -> 16 ignored
Dec  3 11:46:31 pc kernel: [ 9477.745570] capidrv-1: incoming call **15,1,0,16 ignored
Dec  3 11:46:32 pc isdnlog: Dec 03 11:46:32 tei 93 calling ? with ?  PROGRESS: Private network serving local user
Dec  3 11:46:32 pc isdnlog: Dec 03 11:46:32 tei 93 calling ? with ?  PROGRESS: inband information available
Dec  3 11:46:35 pc isdnlog: Dec 03 11:46:35 tei 93 calling ? with ?  HANGUP

```As you see, isdnlog does notice the call.
Of course, you can't see whether the notification pops up, so you have to believe me it doesn't ;-)


Any help?

---

### Post by Lorem on 2010-12-04
bump...

I tried finding any help with google, but the only thing I found were dozens of manpages that I've already read.
It seems tome as if isdnlog would be started without the "start=yes" parameter, but it is in isdnlog.isdnctrl0 which is loaded (I tested this by changing the log file parameter).

---

### Post by Lorem on 2010-12-07
Hm, nobody?

Any other ideas how I could display the caller id using an ISDN card, preferably via libnotify?

---

