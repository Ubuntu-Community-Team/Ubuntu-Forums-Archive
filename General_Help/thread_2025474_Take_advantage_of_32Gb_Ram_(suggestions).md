---
title: "Take advantage of 32Gb Ram (suggestions)"
date: 2012-07-14
forum: General Help
---

### Post by scu-ba-de-buntu on 2012-07-14
For the first time ever I am aware of my computer's slow hard-drive. While I can't afford to get a new solid-state hard-drive, I have a huge amount of ram in this machine. How would people recommend I take advantage of the ram to solve this problem - I remember there used to be bootable OSes that would load onto a "ram-disk" (SLAX, KNOPPIX...) but what about on a permanent Ubuntu install?

---

### Post by Lynch on 2012-07-14
Well... you could mount about 28 GB as a ramdisk (depending on how much your programs use up - check system monitor):
[http://superuser.com/questions/175861/ramdisk-ubuntu-10-04](http://superuser.com/questions/175861/ramdisk-ubuntu-10-04)

I guess, if there's programs or files that you have to access very often you could write rc scripts, that copy them to the ramdisk at startup and back to the harddisk on shutdown or at a certain interval. Of course I wouldn't do it with something that may not get lost (What if the machine crashes before writing everything back?)

OR you could install boinc ( [http://boinc.berkeley.edu/](http://boinc.berkeley.edu/) ) to help fight cancer, find intelligent life in space etc.
It uses some ram (you can configure how much) but usually mostly cpu.

---

### Post by scu-ba-de-buntu on 2012-07-16
I plan to run boinc in the down time. On that note, any suggestions for running it via virtual machine?

---

