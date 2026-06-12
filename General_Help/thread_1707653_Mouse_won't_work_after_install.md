---
title: "Mouse won't work after install"
date: 2011-03-15
forum: General Help
---

### Post by Haltini on 2011-03-15
Hi.

I have recently upgraded to and then reinstalled Maverick (retaining the home directory). After the reinstall the mouse stopped working. It's not a hardware issue as the mouse works fine during the live CD installation. I have tried both a serial and a USB mouse. I have tried reinstalling a couple of times too.

I think I've had this issue before in a previous version but can't remember how I solved it. 

I have been using Ubuntu for about 2 years now, and am by no means an expert. As a result I'm sure you will need more information but am unsure of what information that is or how to get it.

Any help would be greatly appreciated.
Thanks in advance.

-Matthew

---

### Post by flaak_monkey on 2011-03-15
Hopefully this works,

Edit /etc/default/grub, go to the line that begins like:
GRUB_CMDLINE_LINUX_DEFAULT=

Change it to:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"

After that, run this command:
sudo update-grub

Reboot and that's it.

---

### Post by Haltini on 2011-03-15
Thankyou for the response. Unfortunately it did not work. Should I change it back to how it was?

---

### Post by Haltini on 2011-03-16
Sorry to bump my thread like this but if I don't sort this out I'll need to buy a copy of Windows and find Windows alternatives to the Linux programs I am used to using. If I have to do that my upcoming assignments will suffer. I've already lost two days due to this. Needless to say, I'm worried.

---

### Post by digitalf8 on 2011-04-21
Had a problem with USB mouse with gnome on Ubuntu server 10.10. This fixed it right up. Thanks. Haltini, hope you get it to work. Run this and post the block with the mouse handler:
 
cat /proc/bus/input/devices

---

