---
title: "automtic suspend using cron"
date: 2010-10-22
forum: General Help
---

### Post by irmtfan on 2010-10-22
it seems an easy task to suspend a computer in command line
i search through the net and find this:


[LIST]
[*]gksu telinit 0 (shutdown)
[*]gksu telinit 6 (reboot)
[*]gksu /etc/acpi/hibernate.sh (hibernate)
[*]gksu /etc/acpi/sleepbtn.sh (sleep)
[/LIST]
you can replace *gksu* with *sudo*.

i want to suspend my computer at a specific time when im away from home but i have 2 problems in cron that i could not solve it yet.
1- it needs user password (how can i embed the password?)
2- it needs to press a key before suspend.( i want to suspend automatically)
ubuntu 10.04.1

---

### Post by matt_symes on 2010-10-22
Hi,

Run the cron job as the root user. It should not require a password then.

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

Kind regards.

---

### Post by irmtfan on 2010-10-22
Thank you!

the problem #1 is solved now.
but still it needs to press a key before suspend. i think it is related to the sleepbtn.sh codes:
> 
#!/bin/sh

# This script is part of the KEY TRANSLATION part of acpi-support. Compare with
# sleep.sh, which is part of the SUSPEND part of acpi-support. This script is
# intended to translate a key event which is not seen as a suspend key press by
# the rest of the system.


test -f /usr/share/acpi-support/key-constants || exit 0

. /usr/share/acpi-support/key-constants
acpi_fakekey $KEY_SLEEP

also im a bit surprise. i didnt find any thread that explain cron + command line suspend so i create this thread and it means all these years in ubuntu nobody wants to automatically suspend a computer at a specific time. its strange IMHO.

---

### Post by matt_symes on 2010-10-22
Hi,

Have you tried using the "pm-suspend" command (or some such ). Might be just what you are looking for.

man pm-suspend. It has to be run as root.

Kind regards

---

### Post by irmtfan on 2010-10-23
Thank You Very Much!
this is exactly what i want.
hibernating works fine too.

---

### Post by irmtfan on 2010-10-23
sorry now i find another issue.
after suspend (either with command line or click on suspend Icon) when i resume i lost my adsl connections. it is simply could not connect to internet and i have to restart my pc. its strange and seems unrelated but it happen.

---

### Post by matt_symes on 2010-10-23
Hi 

After coming out of suspend open a terminal and type

 sudo /etc/init.d/networking restart

See if this restarts you network.

Kind regards

---

### Post by irmtfan on 2010-10-23
{double post sorry}

---

### Post by irmtfan on 2010-10-23
i did it before without luck. but now i suspend and my connections are ok.
i think its not suspend that damage the connection. it needs more investigation please wait.

---

