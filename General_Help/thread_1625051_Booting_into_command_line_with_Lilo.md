---
title: "Booting into command line with Lilo"
date: 2010-11-18
forum: General Help
---

### Post by Jason Spaceman on 2010-11-18
I'm running Ubuntu 10.10 with Lilo as my boot loader instead of Grub.  I want to boot, temporarily, to a command line prompt instead of X-windows.  How do I do this?  Is there a combination of keys to press when the Lilo screen appears?

---

### Post by sisco311 on 2010-11-18
You have to boot with the **text** kernel parameter. I'm not sure how to edit the enties at boot time, but this should help: [http://tldp.org/HOWTO/LILO-2.html#ss2.3](http://tldp.org/HOWTO/LILO-2.html#ss2.3)

---

### Post by Jason Spaceman on 2010-11-19
OK, typing 'linux single' or 'linux 1' at the Lilo prompt will boot me into another menu that gives me the option of starting X in safe mode, or booting into a command line interface.

---

