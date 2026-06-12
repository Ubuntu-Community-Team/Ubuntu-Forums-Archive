---
title: "sudo halt : the system freezes ; gui shut down is OK"
date: 2011-10-20
forum: General Help
---

### Post by magowiz82 on 2011-10-20
Hi,
since I have more than one pc with ubuntu installed I usually update them using command line via ssh , the problem is that if I give "sudo halt" the shutdown process begins but at one point the pc freezes and the only way to shutdown is to use the power button and then I have to turn on the pc and to shut it down via ligthdm interface. The curious thing is that shutting down via GUI (i.e. ligthdm or unity) works flawlessly .

---

### Post by drofart on 2011-10-20
> **magowiz82 said:**
> Hi,
since I have more than one pc with ubuntu installed I usually update them using command line via ssh , the problem is that if I give "sudo halt" the shutdown process begins but at one point the pc freezes and the only way to shutdown is to use the power button and then I have to turn on the pc and to shut it down via ligthdm interface. The curious thing is that shutting down via GUI (i.e. ligthdm or unity) works flawlessly .
THINK [ IT]("http://ubuntuforums.org/showthread.php?t=1741668") CAN HELP U.


SONA

---

### Post by blackbird34 on 2011-10-20
I use:

sudo shutdown -h now

Everything closes and powers off in about five seconds. (I save and quit programs first, or they are closed too)

---

### Post by magowiz82 on 2011-10-20
> **drofart said:**
> THINK [ IT]("http://ubuntuforums.org/showthread.php?t=1741668") CAN HELP U.


SONA

I don't think so, I have exactly the oppose problem : with GUI it's ok and with CLI KO.

---

### Post by magowiz82 on 2011-10-20
> **blackbird34 said:**
> I use:

sudo shutdown -h now

Everything closes and powers off in about five seconds. (I save and quit programs first, or they are closed too)

With this command it shut down properly, which is the difference between halt and shutdown -h now ?

---

### Post by aeiah on 2011-10-20
from a brief look at the man page for halt, it might be to do with runlevel or something. i always use sudo shutdown -h now (or another time other than 'now')

a quick google indicates that perhaps if your ACPI isn't configured properly, halt won't call shutdown at the end.

---

### Post by pakrat1963 on 2011-10-20
I no longer have a gui shutodwn :( The on/off switch that used to live in the corner is no longer there, so i guess the only way to turn the pc off or reboot will be thru the terminal. Kind of a pain. Does anyone know where to install a new switch?
Thanks, 
pakrat

---

### Post by aeiah on 2011-10-20
you might want to make a new topic, or use google

---

### Post by magowiz82 on 2011-10-21
> **aeiah said:**
> from a brief look at the man page for halt, it might be to do with runlevel or something. i always use sudo shutdown -h now (or another time other than 'now')

a quick google indicates that perhaps if your ACPI isn't configured properly, halt won't call shutdown at the end.

I didn't know that ACPI needs to be configured, I saw that acpid service is running on problematic pc but I have the problem described above. How can I configure ACPI to fix this ?
Anyway before upgrading from 11.04 to 11.10 sudo halt was working flawlessly , I didn't change acpi configuration since then.

---

### Post by magowiz82 on 2011-10-23
I reported this bug : [https://bugs.launchpad.net/ubuntu/+bug/880240](https://bugs.launchpad.net/ubuntu/+bug/880240)

---

