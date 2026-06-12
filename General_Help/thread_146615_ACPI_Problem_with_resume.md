---
title: "ACPI Problem with resume"
date: 2006-03-18
forum: General Help
---

### Post by anandrd on 2006-03-18
I am running Ubuntu 5.10 Breezy on Dell Inspiron 6000 with Intel 915 integrated graphics (if that is relevent). When I try to resume from suspend when I am on battery power, my computer sometimes hangs. I have no messages in /var/log/messages when this happens. My only option is a hard reboot.
I think it is an ACPI problem because I see different messages in /var/log/acpid for successful suspend/resumes and unsuccessful ones. 

For successful suspend/resumes, /var/log/acpid looks like 

```

[Sat Mar 18 17:15:36 2006] received event "button/lid LID 00000080 00000001"
[Sat Mar 18 17:15:36 2006] notifying client 7430[111:111]
[Sat Mar 18 17:15:36 2006] executing action "/etc/acpi/lid.sh"
[Sat Mar 18 17:15:36 2006] BEGIN HANDLER MESSAGES
Setting up swapspace version 1, size = 1480511 kB
no label, UUID=c89a1314-ba31-4827-8abb-2d33131e6bc8
There is already a pid file /var/run/dhclient.eth1.pid with pid 8816
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:13:ce:46:67:e2
Sending on   LPF/eth1/00:13:ce:46:67:e2
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 18.71.0.31 port 67
ERROR: Module battery is in use
xscreensaver-command: no screensaver is running on display :0.0
ERROR: Module fan is in use
ERROR: Module thermal is in use
grep: /proc/acpi/fan/*/state: No such file or directory
[Sat Mar 18 17:15:59 2006] END HANDLER MESSAGES
[Sat Mar 18 17:15:59 2006] action exited with status 0
[Sat Mar 18 17:15:59 2006] completed event "button/lid LID 00000080 00000001"
[Sat Mar 18 17:15:59 2006] received event "ac_adapter AC 00000080 00000000"
[Sat Mar 18 17:15:59 2006] notifying client 7430[111:111]
[Sat Mar 18 17:15:59 2006] executing action "/etc/acpi/power.sh"
[Sat Mar 18 17:15:59 2006] BEGIN HANDLER MESSAGES
[Sat Mar 18 17:15:59 2006] END HANDLER MESSAGES
[Sat Mar 18 17:15:59 2006] action exited with status 0
[Sat Mar 18 17:15:59 2006] completed event "ac_adapter AC 00000080 00000000"
[Sat Mar 18 17:15:59 2006] received event "button/lid LID 00000080 00000002"
[Sat Mar 18 17:15:59 2006] notifying client 7430[111:111]
[Sat Mar 18 17:15:59 2006] completed event "button/lid LID 00000080 00000002"
[Sat Mar 18 17:15:59 2006] received event "battery BAT0 00000081 00000001"
[Sat Mar 18 17:15:59 2006] notifying client 7430[111:111]
[Sat Mar 18 17:15:59 2006] executing action "/etc/acpi/power.sh"
[Sat Mar 18 17:15:59 2006] BEGIN HANDLER MESSAGES
[Sat Mar 18 17:15:59 2006] END HANDLER MESSAGES
[Sat Mar 18 17:15:59 2006] action exited with status 0
[Sat Mar 18 17:15:59 2006] completed event "battery BAT0 00000081 00000001"
There is already a pid file /var/run/dhclient.eth1.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:13:ce:46:67:e2
Sending on   LPF/eth1/00:13:ce:46:67:e2
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 18.74.0.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 18.74.0.1
bound to 18.74.5.116 -- renewal in 1782 seconds.
ifup: interface eth0 already configured

```

For unsuccessful ones, I get

```

[Sat Mar 18 17:08:22 2006] received event "button/lid LID 00000080 00000001"
[Sat Mar 18 17:08:22 2006] notifying client 7060[111:111]
[Sat Mar 18 17:08:22 2006] executing action "/etc/acpi/lid.sh"
[Sat Mar 18 17:08:22 2006] BEGIN HANDLER MESSAGES
Setting up swapspace version 1, size = 1480511 kB
no label, UUID=d7072525-b9ce-4193-930c-888988f31df7
There is already a pid file /var/run/dhclient.eth1.pid with pid 8563
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:13:ce:46:67:e2
Sending on   LPF/eth1/00:13:ce:46:67:e2
Sending on   Socket/fallback
[Sat Mar 18 17:12:34 2006] starting up

```

The last line is when I had to hard reboot.

Can anyone help?

---

### Post by anandrd on 2006-03-21
Bump

---

### Post by jasin on 2007-01-12
seems like you're not the only one with acpi problems, the forums here are plagued with posts about acpi problems. There are work arounds for nearly every acpi problem, but their just that, work arounds.

I guess we need to post more of our acpi problems on launchpad.net in hopes the developers at ubuntu will get off their lazy asses and fix acpi.

---

