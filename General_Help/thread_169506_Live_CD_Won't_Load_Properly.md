---
title: "Live CD Won't Load Properly"
date: 2006-05-02
forum: General Help
---

### Post by obama on 2006-05-02
I recently purchased a Compaq desktop with Pentium processor (2.53 Ghz).  I also burned a Kubunutu Live CD and put it in.  The CD booted up fine, but once I press enter and it starts loading the linux kernel, bad things happen.  It gets to 100% on Loading Linux Kernel, and then the system restarts into Windows.  Can anyone please help?

---

### Post by obama on 2006-05-02
I did the same thing on a different cd drive and with the Debian Live CD.  It performed the same error at the same time.  I think it is trying to boot again once it loads the kernel, and that it's simply booting to the cd again.  Please help.

---

### Post by obama on 2006-05-02
I tried booting in rescue mode but the system immediately started booting Windows.  Please, please help.  Should I perhaps reformat my hard drive and try again?  Any help at all is appreciated.

---

### Post by towsonu2003 on 2006-05-02
there is a good chance the cd is bad. Try checking the md5sum of the iso, than burning it again, with slowest speed. 

don't format the hard drive, LiveCD has nothing to do with the hard disk. It's aim is not to touch it so you can try ubuntu out without commitment.

---

### Post by obama on 2006-05-02
Actually, I solved the problem myself.  I simply had to turn off acpi.

---

### Post by towsonu2003 on 2006-05-02
[QUOTE=obama]Actually, I solved the problem myself.  I simply had to turn off acpi.[/QUOTE]
I should note that for future use :) you passed "acpi=off" to kernel parameters, right?

---

