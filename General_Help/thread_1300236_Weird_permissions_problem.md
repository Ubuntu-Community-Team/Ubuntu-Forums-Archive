---
title: "Weird permissions problem"
date: 2009-10-24
forum: General Help
---

### Post by Cephi on 2009-10-24
I installed Xubuntu (first hardy, then up to jaunty) on the grad lab machine at my school, and there are weird permissions problems.  For example, I only created two user accounts, but under neither of them can I access the Users and Groups dialog; it tells me "You are not allowed to access the system configuration."  And when I try to use mplayer on the command line, I get a long mess of stuff like this:

```

I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[AO_ALSA] alsa-lib: pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused

```

(Relatedly, I can't get any sound whatsoever on this machine, though it's fine in Windows.)

I don't know how to fix this stuff.  When I look online for how to give a user admin privileges, I always see that I'm supposed to use Users and Groups.  But I can't get in to Users and Groups.  Any help appreciated.

---

### Post by Cephi on 2009-10-24
Update: the problem isn't that I lack admin privileges.  I can't run users-admin even as root; I get the same line about not being allowed to access the system config.  When I try it on the command line, I also get:

```

(users-admin:3361): Liboobs-WARNING **: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

(users-admin:3361): Liboobs-WARNING **: OobsSession object hasn't connected to the bus, cannot register OobsObject

(users-admin:3361): Liboobs-WARNING **: OobsSession object hasn't connected to the bus, cannot register OobsObject

(users-admin:3361): Liboobs-WARNING **: OobsSession object hasn't connected to the bus, cannot register OobsObject

** (users-admin:3361): CRITICAL **: Cannot create system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
process 3361: D-Bus library appears to be incorrectly set up; failed to read machine uuid: UUID file '/var/lib/dbus/machine-id' should contain a hex string of length 32, not length 0, with no other text
See the manual page for dbus-uuidgen to correct this issue.

(users-admin:3361): Liboobs-CRITICAL **: oobs_session_get_platform: assertion `priv->connection != NULL' failed

```

I've verified that /var/lib/dbus/machine-id exists but is empty.  Any help appreciated.

---

### Post by Cephi on 2009-10-24
Well, based on what was said here [https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/288596](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/288596) , I deleted the machine-id file and then ran "dbus-uuidgen --ensure" to generate a new one, then rebooted.  That seems to have solved all my problems.

---

