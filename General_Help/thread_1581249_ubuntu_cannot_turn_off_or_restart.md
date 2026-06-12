---
title: "ubuntu cannot turn off or restart"
date: 2010-09-24
forum: General Help
---

### Post by behzadsh on 2010-09-24
hi,
I don't remember when it started, my ubuntu hang when trying to shut down...

I tried every possible way to shut down, by command, poweroff, reboot, halt and ...
In verbose mode the last message is:
```

init: rc main process ((process id e.g. "26350")) killed by TERM single

```

and only way I have, to turn off is "Alt + Ctrl + delete"... and when I press them this message appear for a while then restart:
```

waiting for running unattended-updates:
... 

```

what's wrong?

---

### Post by andrewthomas on 2010-09-24
try 
```

sudo shutdown -r now
```to reboot

and 

```
sudo shutdown -h now
``` to shutdown

then when you reboot
```

sudo aptitude update && sudo aptitude safe-upgrade
```

---

### Post by behzadsh on 2010-09-25
Didn't work! :(

---

### Post by Alexis Phoenix on 2010-09-25
Does the start of this problem coincide with you getting some new hardware, perhaps?
Other things I can think of to check:
/etc/fstab - is all well in there?
Is your hard disk root partition getting full?```
df -h /
```There needs to be enough space for logging to take place at least
New bios settings at some point?
Have you tried stopping X and then shutting down?
Can you find the log entries for when the computer was trying to shut down, see if there is anything strange before that final "rc main process" message - maybe some clue in there?
HTH

---

### Post by Quackers on 2010-09-25
Are any usb peripherals plugged in at the time?

---

### Post by behzadsh on 2010-09-26
@Alexis Phoenix: You asked a lot of thing :D
> **Alexis Phoenix said:**
> 
Does the start of this problem coincide with you getting some new hardware, perhaps?

Nope

> **Alexis Phoenix said:**
> 
/etc/fstab - is all well in there?

yes

> **Alexis Phoenix said:**
> 
Is your hard disk root partition getting full?```
df -h /
```There needs to be enough space for logging to take place at least

yes it has 8.2 GB free + 2GB swap

> **Alexis Phoenix said:**
> 
New bios settings at some point?

No

> **Alexis Phoenix said:**
> 
Have you tried stopping X and then shutting down?

No

> **Alexis Phoenix said:**
> 
Can you find the log entries for when the computer was trying to shut down, see if there is anything strange before that final "rc main process" message - maybe some clue in there?

I couldn't find, maybe I don't know where exactly I have to look


> **Quackers said:**
> Are any usb peripherals plugged in at the time?
not all the time, when I'm home or office I plug an external usb hard drive, but without plugging it I have the same problem.


I remember I had this problem before and it solved, but don't remember how? :confused:

---

