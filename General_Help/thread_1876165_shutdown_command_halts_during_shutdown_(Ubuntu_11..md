---
title: "shutdown command halts during shutdown (Ubuntu 11.10)"
date: 2011-11-05
forum: General Help
---

### Post by necrosmash on 2011-11-05
I couldn't find someone with the same problem as me, so hopefully this isn't duplicated...

Anyway, I want to shut down my netbook at a specific time by using the shutdown command. However, every time I try to use the shutdown command (whether it be attempting to shut it down immediately or at a specified time), my netbook halts when the onscreen log shows "disabling power management..." as the last entry.

Does anyone have any recommendations regarding how I could automatically shut down the system at a specific time?

---

### Post by llamabr on 2011-11-05
Depends.  What command are you using?

---

### Post by necrosmash on 2011-11-05
Just the bog-standard shutdown one. When I want to shut down the system immediately, I use

```
sudo shutdown 0
```

or to shut it down at, say, 23:30

```
sudo shutdown 23:30
```


Any suggestions?

---

### Post by LinuxFan999 on 2011-11-05
Is this a clean install of Ubuntu 11.10, or did you upgrade from an earlier version?

---

### Post by necrosmash on 2011-11-05
Thank you both for your input! This is a fresh install of Ubuntu 11.10.

For what it's worth, I've also tried using GShutdown, but all that succeeds in doing is logging me out of my current session instead of shutting the system down.

**EDIT:** Problem solved, perhaps I should have played around with the command more. Anyway, I got it working by using the -h switch. For example:

```
sudo shutdown -h 23:50
```

---

### Post by llamabr on 2011-11-05
right.  -h for 'halt' and -r for reboot.  I typically give it a:

```
sudo shutdown -h now
```

if I want it now, or something like:

```
sudo shutdown -h 90
```

for 90 seconds from now.

---

