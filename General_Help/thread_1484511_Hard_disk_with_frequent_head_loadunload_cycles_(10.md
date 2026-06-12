---
title: "Hard disk with frequent head load/unload cycles (10.04)"
date: 2010-05-15
forum: General Help
---

### Post by dementic on 2010-05-15
Hello,

I have a problem in Ubuntu 10.04. The bug is well know which makes the hard disk head to park often (2-3 times per minute) that's dangerous for the drive in the long term and annoying for me (click-click-click).

I found out the "ugly-fix" for old Ubuntu version which was :

hdparm -B 254 /dev/sda instead of 128. It works. 

The problem is that it doesn't remains (when restart/standby/ac connection-disconnection).

I found a script well known too :

```

1) make a file named "99-hdd-spin-fix.sh". The important thing is starting with "99".
2) make sure the file contains the following 2 lines (fix it if you have PATA HDD):
#!/bin/sh
hdparm -B 255 /dev/sda
3) copy this file to 3 locations:
/etc/acpi/suspend.d/
/etc/acpi/resume.d/
/etc/acpi/start.d/

```

The problem is that suspend.d, resume.d, start.d doesn't seems to be used anymore so it doesn't work. Anyone has a solution?

Thank you!

---

### Post by dementic on 2010-05-16
no one?

---

### Post by dpologea on 2010-06-14
I have encountered this problem too. I know about it for a long time by now and I would be interested to find a solution for Ubuntu 10.04.
I have a netbook with Ubuntu Netbook Edition.

Thanks.

---

### Post by SabreWolfy on 2010-06-14
Anything to do with [this]("https://bugs.launchpad.net/bugs/568120")?

---

### Post by sdennie on 2010-06-14
2-3 times a minute is nothing to worry about if it's a laptop (2.5") disk.  Even a desktop (3.5") disk is probably fine at 2-3 clicks a minute.  The problem you are thinking of is where the disk would generally click every 5-10 seconds and even that was probably blown out of proportion.  However, if you'd like to make your hdparm settings permanent, the equivalent directories in modern Ubuntu releases are /etc/pm/sleep.d and /etc/pm/power.d.

---

