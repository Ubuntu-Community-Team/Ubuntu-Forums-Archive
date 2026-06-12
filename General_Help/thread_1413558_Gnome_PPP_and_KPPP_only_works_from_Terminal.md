---
title: "Gnome PPP and KPPP only works from Terminal"
date: 2010-02-22
forum: General Help
---

### Post by heylookitsmewow on 2010-02-22
I just installed 9.10 and this is my first time using Ubuntu. I was using Kubuntu before and used KPPP with my Verizon USB720 wireless card. It's the type that gets internet access through the cell towers.

I installed KPPP but when I try to start it I get this error:

> Could not launch KPPP
Failed to execute child process (permission denied)

I tried Gnome PPP and it would open but not connect. This is what is in my log files"


> --> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.

After doing much searching and reading I figured out to open Gnome PPP from the terminal with sudo. When I do that it works fine. Also KPPP opens that way although I haven't tried it to see if it connects. 

Although this works it's not a very convenient way to connect. How can I get it to work without doing this?

---

### Post by nixclusive on 2010-02-22
Ideally this should work out of the box but here's a workaround anyway:

1. Determine the file permission on the ppp daemon:
```
$ls -l /usr/sbin/pppd
```

on my system the above command gives the output:
```
-rwsr-xr-- 1 root **dip** 321600 2009-02-20 23:56 /usr/sbin/pppd
```

the highlighted field is the group permission of that file.

2. Add yourself to this group:
```
sudo adduser `whoami` **dip**
```

---

### Post by heylookitsmewow on 2010-02-22
That worked for Gnome PPP. 

Now KPPP gives this error

> kppp can not create or read from /home/me/.kde/share/apps/kppp/kppp.pid

I am guessing maybe it's because I don't have kde installed. Since Gnome PPP is working fine now I will probably just remove KPPP anyway so that problem doesn't really matter.

Thanks for the help.

---

