---
title: "Synce stopped working"
date: 2010-04-30
forum: General Help
---

### Post by Artiom.Fiodorov on 2010-04-30
Upgraded to 10.04. Added new repository, updated synce
when I run synce-pls I get this message:

synce-pls

** (process:8144): CRITICAL **: synce_info_from_hal: Failed to initialise hal context: (null): (null)
process 8144: Attempt to remove filter function 0x7f95081d3d90 user data 0x23d6e90, but no such filter has been added
** Message: Odccm is not running, ignoring

Anyone?

---

### Post by Artiom.Fiodorov on 2010-04-30
My bad. Just updated everything again and restarted. It worked.

---

### Post by khalidabuu on 2010-05-01
Hey i have this problem to i restarted and tried to see if it would work it showed synce but no i couldnt search the files nor did multisync sync correctly. In the synaptics package manager some of the dependencies are out of date but wont update it says python(<2.6) but 2.6.5 is to be installed. Help.

---

### Post by gurukreff on 2010-05-12
> **Artiom.Fiodorov said:**
> My bad. Just updated everything again and restarted. It worked.
I have the same problem, but it didn't solve itself just by updating and restarting. I, on the other hand, i'm using a clean lucid install, fully updated, and have tho followind output from the synce-pls command:

** (process:1497): CRITICAL **: synce_info_from_hal: Failed to initialise hal context: (null): (null)
process 1497: Attempt to remove filter function 0x7fee70783d90 user data 0x11b2e90, but no such filter has been added
** Message: Odccm is not running, ignoring
synce-pls: Could not find configuration at path '(Default)'


Wich is the same that Artiom had, does anyone know how to fix this?

---

### Post by mpshab on 2010-05-19
Same problem.

HTC TP2 wm 6.5
Ubuntu Lucid.  I checked the software and it all Lucid, and latest version.

** (process:2993): CRITICAL **: synce_info_from_hal: Failed to initialise hal context: (null): (null)
process 2993: Attempt to remove filter function 0xfbc6c0 user data 0x9760848, but no such filter has been added
** Message: Odccm is not running, ignoring
synce-pls: Could not find configuration at path '(Default)'

I've tried almost everything I can think of.. 
One thing; when I put the phone in "data mode "  ubuntu recognizes it as a usb srive, and I can access the SD card.

---

