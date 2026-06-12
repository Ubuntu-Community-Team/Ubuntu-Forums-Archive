---
title: "Does acpid duplicate BIOS functions?"
date: 2006-05-04
forum: General Help
---

### Post by Patb on 2006-05-04
I understand that the acpid (acpi daemon) is for power management and CPU temperature control.  If I have set the BIOS to shutdown if the temperature exceeds a certain temperature, is there any point in having the acpid running?  Is it not doing the same job as the BIOS is doing?  Or does it have some additional function?  I have a 2.4 Ghz Celeron desktop PC running dual boot Win98/Ubuntu 5.10.  Comments/enlightenment appreciated.  

Thanks, Pat.

---

### Post by shof2k on 2006-05-04
ACPI allows Ubuntu to have hardware control.  I don't know the exact BIOS you have, but my guess is that when your temperature limit is exceeded, your machine will simply stop without paying attention to whats running.

ACPI lets the OS control what to shut down and when giving a 'smooth landing'.  ACPI can also control other stuff like spinning down the disks, suspend, and hibernate but that depends on how well ACPI is running.

---

### Post by Patb on 2006-05-05
Thanks for the explanation Shof.  The reason for my enquiry was that I was looking for processes which I could disable in order to improve speed of booting.  From your response, it would seem unwise to disable acpid.  If I did have an overheating problem, it would be nice to be given a 'smooth landing' (which my BIOS would almost certainly not give).  

Cheers, Pat.

---

### Post by shof2k on 2006-05-05
Try the following articles:
[http://www.ubuntuforums.org/showthread.php?t=80423](http://www.ubuntuforums.org/showthread.php?t=80423)
[http://www.ubuntuforums.org/showthread.php?t=89491](http://www.ubuntuforums.org/showthread.php?t=89491)

---

