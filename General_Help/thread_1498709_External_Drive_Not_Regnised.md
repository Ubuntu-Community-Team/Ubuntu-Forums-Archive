---
title: "External Drive Not Regnised?"
date: 2010-06-01
forum: General Help
---

### Post by johnkelly.110 on 2010-06-01
I am relatively new to Ubuntu 10.4 - I am experimenting with back-ups trying to use either Deja Dup or Simple Backup.
My External Drive which worked well with Vista is UNrecognised by Ubuntu 10.4.
HELP!

---

### Post by shai3421 on 2010-06-01
Did you try to connect it to other USB ports?

---

### Post by johnkelly.110 on 2010-06-01
Yes - nothing shows up!

---

### Post by dino99 on 2010-06-01
you need pmount and usbmount installed, mountmanager is the easy way to deal with partitions and devices (tweak it in "system admin mountmanager"

---

### Post by johnkelly.110 on 2010-06-01
> **dino99 said:**
> you need pmount and usbmount installed, mountmanager is the easy way to deal with partitions and devices (tweak it in "system admin mountmanager"
Where is this?

---

### Post by dino99 on 2010-06-01
> **johnkelly.110 said:**
> Where is this?

to install the packages: goto menu "system admin synaptic" and search for the package. If synaptic is not installed, from a console (apps terminal), run the command:

sudo apt-get install synaptic

---

### Post by johnkelly.110 on 2010-06-01
THANKS! i'LL TRY THAT!

---

### Post by johnkelly.110 on 2010-06-01
I installed pmount and usbmount still not recognising my external hd?

---

### Post by Jeroensum on 2010-06-01
What does lsusb tell you and what does dmesg show when you plugin the drive?

In a terminal run: dmesg
Then plugin your drive
Run dmesg again and see if it states something about an usb device

While the drive is plugged in run lsusb and check what it states there about the drive.

---

