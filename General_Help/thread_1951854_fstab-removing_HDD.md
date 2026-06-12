---
title: "fstab-removing HDD"
date: 2012-04-03
forum: General Help
---

### Post by eawz9999 on 2012-04-03
I used to have 4 HDD connected in my Ubuntu 11.04, sda, sdb, sdc and sdd (my USB drive), I removed sdc. My HDD are mounted automatically in fstab using UUID=.
On reboot my HDD show as sda, sdb and sdc (my USB). Without rebooting, at times I get an **input/output error** on sdc. If I check my configuration my USB drive appears as “not mounted” and the designation of sdd, the same drive is mounted as sdc but not accessible.  I can manually mount sdd and it works fine.
My question is where and when is this drive designation been changed? After removing 1 HDD, do I have to change anything else beside fstab? My server is on 24/7, what program is changing the HDD designation?
Thank you, Enrique

---

### Post by eawz9999 on 2012-04-03
For some reason, after I posted the question a possible explanation occurred to me.
My USB drive is not connected to my battery backup system as is my server. It is possible that a brief power blackout is turning my USB drive off. When power is restore the server is not remounting the drive where it was?

---

### Post by eawz9999 on 2012-04-11
**That was the problem**. A brief power blackout (not uncommon in Florida) was taking the USB drive off line. When it came back on, Ubuntu will recognize it and assigned the next drive designation but not mount it since it was not unmounted when it went off line.

---

### Post by callmemahavir on 2012-04-11
It is sure that your pen drive in sdd after boot assigned to sdc. 
Try installing the sdc in the same mount point as sdd before. (As sdd before).

What happened is usb drives are reordered after boot (names are reorded).

The solution is which device name goes to which mount point.

---

### Post by bab1 on 2012-04-11
> **eawz9999 said:**
> **That was the problem**. A brief power blackout (not uncommon in Florida) was taking the USB drive off line. When it came back on, Ubuntu will recognize it and assigned the next drive designation but not mount it since it was not unmounted when it went off line.
You can name the USB device and mount it by name.  See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www.reactivated.net/writing_udev_rules.html") for details.

---

### Post by eawz9999 on 2012-04-11
Thank you very much for your interest. The problem was solved by plugging the USB to the battery backup system. The USB is mounted by its universally unique identifier during boot (fstab) and is always mounted in the same place (as sdc, sdc1, etc1). This problem was not only bad for my cron jobs but also bad for the HDD).
Thank you again, Enrique

---

