---
title: "where do I find the logs for programs started with &quot;Startup Applications&quot;?"
date: 2010-10-05
forum: General Help
---

### Post by geometrikal on 2010-10-05
I have a program that runs fine from the terminal, but when I put it into the Startup Applications it doesn't work. Where can I check the logs to see what the problems is?

By the way, this is the command:

bash -c "sudo dbus-launch path_to_program --debug > path_to_debug.log"

Thanks

---

### Post by mikewhatever on 2010-10-05
You can't use sudo with startup applications. Use gksudo instead, or else, /etc/rc.local to run the command without sudo.

---

### Post by geometrikal on 2010-10-06
thanks heaps for your help

---

