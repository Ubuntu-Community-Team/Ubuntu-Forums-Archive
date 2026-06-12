---
title: "Various Services Not Starting at Boot"
date: 2010-08-04
forum: General Help
---

### Post by Warthaug on 2010-08-04
I am running ubuntu 10.04, 64bit.  I am having an issue with several manager-type applications not starting at boot.  CUPS, boinc clients and the virtual box kernel manager often do not start at boot (although they do, sometimes - gotta love intermittent errors!).

My current "fix" is a script which starts boinc and CUPS (but not the vbox kernel driver).  I'd like to come up with a proper fix.  So, my Q's:

1) Anyone know why this may be happening, and how to fix this?  
2) I assume there is a master file that lists all of the processes started at boot.  What is the name of the file, and where do I find it?
3) Does anyone know how to start the vbox kernel driver without recompiling it.

Thanx in advance, for any help you guys/gals can give.

Bryan

---

### Post by Fafler on 2010-08-04
1. Could be network related. If you use a DHCP server and it is slow to give an IP address, some services may fail to start.

2. The startup scripts are placed in /etc/init.d/ and linked to /etc/rc2.d to be run at startup. Only scripts starting with S are executed and the 2 digits after mandates the order, eg. /etc/rc2.d/S25bluetooth runs before /etc/rc2.d/S50cups.

---

### Post by Warthaug on 2010-08-04
> **Fafler said:**
> 1. Could be network related. If you use a DHCP server and it is slow to give an IP address, some services may fail to start.

2. The startup scripts are placed in /etc/init.d/ and linked to /etc/rc2.d to be run at startup. Only scripts starting with S are executed and the 2 digits after mandates the order, eg. /etc/rc2.d/S25bluetooth runs before /etc/rc2.d/S50cups.

#1 sounds very plausible - I tend to have this problem at work, not at home, and it got worse after we expanded the wireless network at work with a couple of access points.

Now, is there any way to prevent this problem?  Can I set the "ask for IP address" task to the end of the boot process, or throw a delay in there to give the server time?

Thanx

Bryan

---

### Post by Warthaug on 2010-08-04
Here is what is listed under /etc/rc2.d:

```

S20speech-dispatcher  S50rsync         S99acpi-support
S20boinc-client       S20vboxdrv       S50saned           S99grub-common
S20fancontrol         S25bluetooth     S70dns-clean       S99ondemand
S20gdomap             S50cups          S70pppd-dns        S99rc.local
S20kerneloops         S50pulseaudio    S90binfmt-support
```

What is odd is that the processes which are failing (S20boinc-client, S20vboxdrv, S50cups) are scattered in the list, and appear to start before the DNS services (S70dns-clean and S70pppd-dns).

Do you think this may be fixable by moving boinc/vboxdrv/cups to a higher value (i.e. S99 or something like that)?

Thanx

Bryan

---

