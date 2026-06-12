---
title: "Waking up ubuntu at a certain time."
date: 2009-11-23
forum: General Help
---

### Post by Johndo1 on 2009-11-23
I need some help. 
I would like to make my computer wake up at a certain time with the sound of music. I tried using apmsleep but it gives me:

apmsleep: Your kernel does not support APM.
apmsleep: Recompile kernel with APM and /dev/rtc support

I was told that this would fix it:
echo "+00-00-00 00:03:00" > /proc/acpi/alarm

The result was: /proc/acpi/alarm: no such file or directory.

Should I create my own /proc/acpi/alarm file with an mp3 file in it and try?
Does Ubuntu 9.10 work with apmsleep? (although I doubt it.)
Any suggestions/advice are appreciated. 

Additional Details.
I'm running ubuntu 9.04

---

### Post by Aflack on 2009-11-23
try alarm clock from the software center, i used to use it.

---

### Post by Johndo1 on 2009-11-25
I'm currently using that but I'd rather decrease the strain on my laptop. Oh well looks like I'll have to cope...

---

### Post by sedawk on 2009-11-25
Do you have a working ACPI-structure, e.g.
/proc/acpi/battery/BAT0/... ?

(May be ACPI doesn't work on your laptop or needs to
 be enables via the kernel parameter "apci=force" )

Wake-on-Clock only works if the BIOS supports it.
Check if your bios supports it or if you have to
enable it first.

---

