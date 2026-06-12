---
title: "Shutdown hangs since upgrade to 11.10"
date: 2011-10-20
forum: General Help
---

### Post by Sentynel on 2011-10-20
Since updating to 11.10, the shutdown process hangs near the end. Events are as follows:

KDE/X exit successfully. The splash screen shows briefly, then is replaced with a console full of text, which is cleared before I can read anything. It hangs on this blank screen.

I can switch TTY successfully. TTY1 shows the standard init messages (various processes exiting, etc) and nothing else.

I'm unable to log into any TTY, as they don't respond to keyboard input, so I can't check what processes are still running.

/var/log/dmesg doesn't seem to have anything useful in:
```
[20:25:11][sam@archimedes:~]$ cat /var/log/dmesg | tail
[   11.272555] type=1400 audit(1319128196.201:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1097 comm="apparmor_parser"
[   11.272844] type=1400 audit(1319128196.201:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1097 comm="apparmor_parser"
[   11.273026] type=1400 audit(1319128196.201:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1097 comm="apparmor_parser"
[   11.278689] type=1400 audit(1319128196.205:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1103 comm="apparmor_parser"
[   11.282441] type=1400 audit(1319128196.209:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=1104 comm="apparmor_parser"
[   11.284698] type=1400 audit(1319128196.213:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1114 comm="apparmor_parser"
[   11.285171] type=1400 audit(1319128196.213:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1114 comm="apparmor_parser"
[   11.368700] init: failsafe main process (1038) killed by TERM signal
[   11.381505] init: apport pre-start process (1182) terminated with status 1
[   11.394218] init: apport post-stop process (1254) terminated with status 1
```
I'm at a bit of a loss for other information to look for to debug this. Does anybody have any ideas?

---

### Post by Sentynel on 2011-10-23
I managed to get a picture of the kernel trace that shows during shutdown. I don't know if it's any use.
[[IMG]http://img694.imageshack.us/img694/5304/img20111021121445.th.jpg[/IMG]]("http://img694.imageshack.us/i/img20111021121445.jpg/")

---

### Post by davetib on 2011-11-16
I know this is an old post, but I figured I'd let you know what I did to get around this error. 

I upgraded from Kubuntu 11.04 to 11.10 and when attempting a shutdown, the system would hang on the Kubuntu splash screen.

Here's what I did.

System Settings
Under System Administration Choose:
Login Screen
Click the Shutdown tab. 
Change the HALT behaviour from:
/sbin/halt TO  /sbin/shutdown -P now

That corrected the problem for me.

Cheers,
Dave

---

### Post by Sentynel on 2011-11-16
The issue for me turned out to be screwy wifi drivers. Changed to a different antenna and my problems went away.

---

### Post by badnack on 2011-11-16
> **davetib said:**
> I know this is an old post, but I figured I'd let you know what I did to get around this error. 

I upgraded from Kubuntu 11.04 to 11.10 and when attempting a shutdown, the system would hang on the Kubuntu splash screen.

Here's what I did.

System Settings
Under System Administration Choose:
Login Screen
Click the Shutdown tab. 
Change the HALT behaviour from:
/sbin/halt TO  /sbin/shutdown -P now

That corrected the problem for me.

Cheers,
Dave

Excuse me whereas i've the same problem on ubuntu 11.10, do you know where i can change the behaviour of halt in my case?

---

### Post by davetib on 2011-11-16
> **badnack said:**
> Excuse me whereas i've the same problem on ubuntu 11.10, do you know where i can change the behaviour of halt in my case?

I'm guessing Ubuntu has a similar System Settings feature. But, sorry, I've only got Kubuntu loaded on a couple of boxes here.

---

### Post by quornian on 2011-11-23
Having the same problem with my Belkin Wireless G dongle.

It seems limited to the 64bit installation (tried 32bit with and it worked fine with no problems).

It also hangs if I pull out the dongle.

For more info, see the bug report: [https://bugs.launchpad.net/bugs/828548](https://bugs.launchpad.net/bugs/828548)

Will try to see if I can find the equivalent setting for Ubuntu as davetib mentions for Kubuntu. Would like to find a driver fix too though.

---

### Post by oldtimer7777 on 2011-11-23
Did you contact Belkin support to ask them? It is free to call and ask them.

> **quornian said:**
> Having the same problem with my Belkin Wireless G dongle.

It seems limited to the 64bit installation (tried 32bit with and it worked fine with no problems).

It also hangs if I pull out the dongle.

For more info, see the bug report: [https://bugs.launchpad.net/bugs/828548](https://bugs.launchpad.net/bugs/828548)

Will try to see if I can find the equivalent setting for Ubuntu as davetib mentions for Kubuntu. Would like to find a driver fix too though.

---

### Post by sleky on 2011-12-09
> **davetib said:**
> I know this is an old post, but I figured I'd let you know what I did to get around this error. 

I upgraded from Kubuntu 11.04 to 11.10 and when attempting a shutdown, the system would hang on the Kubuntu splash screen.

Here's what I did.

System Settings
Under System Administration Choose:
Login Screen
Click the Shutdown tab. 
Change the HALT behaviour from:
/sbin/halt TO  /sbin/shutdown -P now

That corrected the problem for me.

Cheers,
Dave

Mine is:

```
/sbin/shutdown -h -P now
```

Why would you omit the 'halt'?

Also....  (Forgive my lack of knowledge atm) But - Is there a way to save the *[color=blue]var/log/dmesg[/color]* after each session?  I checked the man page, but there wasn't much in there in way of logging.  And checking my current file didn't give much in the way of shedding any light why it would lock up.

EDIT:  Well.  **sudo shutdown -h now** works like a champ.  I can live with that.  =]

---

