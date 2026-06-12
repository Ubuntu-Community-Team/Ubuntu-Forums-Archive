---
title: "sleep.sh turns on my ethernet card"
date: 2009-10-28
forum: General Help
---

### Post by editrix on 2009-10-28
I have just learned that the way to prevent screen flicker after suspending my computer is to use **sudo /etc/acpi/sleep.sh**

Only problem now is, when it wakes up, my ethernet card is turned on. This is a PITA, as I use a dialup modem, and I have to turn the ethernet off by using **sudo ifdown  eth0**.

The message I get is:

> sudo /etc/acpi/sleep.sh

 * Shutting down ALSA...                                                 [ OK ]
 * Saving the system clock
/etc/acpi/resume.d/17-video-restore.sh: line 5: /var/lib/acpi-support/vbestate: No such file or directory
Function not supported
 * Setting the system clock
 * Setting up ALSA...                                                    [ OK ]
FATAL: Module acpi_sbs not found.
FATAL: Module acpi_sbs not found.

I can't rip the card out, as I use it to connect to another computer in-house.

Can anyone help a total ignoramus on this?

---

