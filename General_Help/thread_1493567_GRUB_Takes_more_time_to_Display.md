---
title: "GRUB Takes more time to Display"
date: 2010-05-26
forum: General Help
---

### Post by aditya.gnu on 2010-05-26
Dear Ubuntu Geeks,
I have installed Ubuntu 9.10 on my PC ie AMD Athlon x64 with 15 GB for \(root)   partition and 2 gb for Swap Space,with 1.2 GB of RAM,but after the   successful installation its not displaying the GRUB immediately, taking   90-270 seconds to display? What might be the reason.?

I have windows XP on my pc,even for booting into Win XP, one needs the   GRUB display, its taking almost 90-180 Seconds to display the   GRUB(sometimes more than that).

But this thing never used to happen in previous versions of Ubuntu? Why   only for this specific Ubuntu 9.10? 

Kindly give me some alternative solution to reduce the GRUB Display   timings.

Thanks & Regards,
Aditya.

---

### Post by sdennie on 2010-05-26
The execution of Grub is outside the realm of the OS.  It's just a very small "OS" that lives in the boot sector.  If you are seeing very long load times before even getting to the grub menu, it's possible your disk is dying.

---

### Post by aditya.gnu on 2010-05-28
Thanks for the suggestion dear friend, but What would be the appropriate solution for my problem.
Somebody please do reply.

Regards,
Aditya.

---

### Post by sdennie on 2010-05-28
I would try booting from the CD/USB stick that you installed from.  If grub comes up quickly booting from something other than the hard drive then it's probably a hard drive or installation problem.  If it comes up just as slow then it's certainly a hardware problem.

---

### Post by aditya.gnu on 2010-05-28
I will try it as you have said and post the scenario.

---

