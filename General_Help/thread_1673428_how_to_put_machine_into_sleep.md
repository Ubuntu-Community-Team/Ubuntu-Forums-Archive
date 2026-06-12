---
title: "how to put machine into sleep"
date: 2011-01-22
forum: General Help
---

### Post by xiongnu on 2011-01-22
hi guys

i'm trying to figure out how to put my ubuntu 7.04 to sleep

when i run 
'su pmi action suspend' 

i got following output:

:popcorn:
erdos@erdos-desktop:~$ su pmi action suspend
Unknown id: pmi
erdos@erdos-desktop:~$ sudo pmi action suspend
Password:
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth2.pid with pid 5118
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth2/00:04:5a:8e:fa:ee
Sending on   LPF/eth2/00:04:5a:8e:fa:ee
Sending on   Socket/fallback
DHCPRELEASE on eth2 to 10.10.10.1 port 67
There is already a pid file /var/run/dhclient.eth3.pid with pid 3594
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth3/00:09:5b:68:4e:68
Sending on   LPF/eth3/00:09:5b:68:4e:68
Sending on   Socket/fallback
DHCPRELEASE on eth3 to 10.10.10.1 port 67
ifdown: interface eth2:avah not configured
SIOCSIFFLAGS: Cannot assign requested address
 * Shutting down ALSA...                                              [ OK ] 
/etc/acpi/sleep.sh: line 39: echo: write error: No such device
/etc/acpi/resume.d/17-video-restore.sh: line 5: /var/lib/acpi-support/vbestate: No such file or directory
Function not supported
ifup: interface eth2 already configured
ifup: interface eth3 already configured
Ignoring unknown interface eth2:avah=eth2:avah.
 * Setting up ALSA...                                                 [ OK ] 
FATAL: Module acpi_sbs not found.
FATAL: Module acpi_sbs not found.
erdos@erdos-desktop:~$

---

### Post by 3602 on 2011-01-22
Feisty? I think at this point it is better to backup all your data then do a fresh install of either Lucid or Maverick.

---

### Post by xiongnu on 2011-01-26
yeah,  I'm running Ubuntu on an old Dell PC.  I mainly use it to surf online and e-mail stuff.  Updating might go way beyond its capability.:)

is suspend/sleep working properly in Lucid or Maverick?

---

### Post by claracc on 2011-01-27
In lucid lynx, I use the command :  sudo pm-suspend, terminal asks for root password and then computer goes to sleep.

Of course, you have to have the software package pm-utils installed.

---

### Post by clhsharky on 2011-01-27
xiongnu

Try Lubuntu

Sharky

---

