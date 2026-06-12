---
title: "Maxtor External Automagic button"
date: 2011-11-06
forum: General Help
---

### Post by Fred Doolie on 2011-11-06
The HDD light on my Maxtor USB external is also a pushbutton that triggers the Windows Maxtor backup software.

Any way to have Ubuntu watch for that button and launch something like Clonezilla or whatever?

---

### Post by kgas on 2011-11-06
I am not sure about this. You can check dmesg | tail out put for the action of pressing the button. If it is registered you can write a script to do the backup.

---

