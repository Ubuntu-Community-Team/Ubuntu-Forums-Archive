---
title: "Resume from sleep displays static"
date: 2011-07-14
forum: General Help
---

### Post by guy_smiley:) on 2011-07-14
Hi,
Currently running 11.04 Ubuntu 64bit. Installed on an H55 motherboard with an i3 therefore running onboard graphics via HDMI. When I wake the PC from suspend, the display only shows static (white noise) like that of an old analog tv with no reception.

Changing channels on the receiver displays the desktop (XBMC autostart) for a brief flash before it goes to the new input.

I have tried adding the following into /etc/default/grub;
"acpi_osi=Linux" and updating grub to no avail. I have tried the workaround by adding another file "20_" into /etc/pm/sleep.d/ again to no avail.

Any help would be much appreciated.

NB: this is white noise/static not a blank screen.

---

### Post by guy_smiley:) on 2011-07-16
No one has experienced this before? I remember having a similar issue on different hardware. Can anyone point me in the direction of disabling the display driver on sleep and re-enable it on wake?

---

### Post by guy_smiley:) on 2011-07-27
Bump? Any ideas or help please?

---

