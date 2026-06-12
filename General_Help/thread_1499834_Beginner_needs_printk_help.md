---
title: "Beginner needs printk help"
date: 2010-06-02
forum: General Help
---

### Post by pauldemet on 2010-06-02
I have written a Linux device driver and need assistance with the printk command.
 
I am trying to us the printk command to ouput data during driver execution. For some reason, I cannot get any output to any log file.
 
After boot, I can see the ouput of printk messages within the initialization module by using the dmesg command. But no other printk messages are ever executed (I think).
 
Any assistance would be appreciated.

---

### Post by xolot1 on 2010-06-02
In what logs are you looking?

A **printk** command like:

```
printk(KERN_DEBUG "Hello world\n");

```
would go to */var/log/debug*.


You might find this message useful: 
[http://www.wplug.org/pipermail/wplug/2002-November/014975.html]("http://www.wplug.org/pipermail/wplug/2002-November/014975.html")

---

### Post by pauldemet on 2010-06-02
None of my printk messages go to this file. The intialization printk statements are output to the dmesg buffer but no other printk statements make it that far.

---

