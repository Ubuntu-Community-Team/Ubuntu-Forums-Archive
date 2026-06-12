---
title: "The clock on the desktop is 6 hours behind sys clock"
date: 2010-01-09
forum: General Help
---

### Post by DXM31 on 2010-01-09
I am running 9.10
Like the title says, I have tried setting it manually but that just messes up the sys clock. So I set it back to use servers.
When I boot to windows 7 the time is right.
I have seen another thread about time, but mine was right up until I loaded 7 and redid grub.

---

### Post by michy99 on 2010-01-09
Read this thread:

[http://ubuntuforums.org/showthread.php?t=960963](http://ubuntuforums.org/showthread.php?t=960963)

---

### Post by DXM31 on 2010-01-09
> **michy99 said:**
> Read this thread:

[http://ubuntuforums.org/showthread.php?t=960963](http://ubuntuforums.org/showthread.php?t=960963)

I read the thread and that is my problem, but the thread that is pointed to in that thread, doesn't mention anything about how to change UTC,
Thanks, and I will search how to set UTC to not.

---

### Post by michy99 on 2010-01-09
Open /etc/default/rcS for editing.```
gksudo gedit /etc/default/rcS
```Change utc line to```
UTC=no
```(if it already = no, try changing it to yes.) Save and exit. You may have to reboot for it to take effect.

---

### Post by DXM31 on 2010-01-09
> **michy99 said:**
> Open /etc/default/rcS for editing.```
gksudo gedit /etc/default/rcS
```Change utc line to```
UTC=no
```(if it already = no, try changing it to yes.) Save and exit. You may have to reboot for it to take effect.

I changed it from yes to no rebooted still the same 6 hours behind

---

### Post by michy99 on 2010-01-09
Do you have the correct time zone setting in System->Administration->Time and Date?

---

### Post by DXM31 on 2010-01-09
Yes, it is also set to use servers and the server is also in my time zone

---

### Post by michy99 on 2010-01-09
Well you got me stumped. Maybe someone else has an idea.

---

### Post by DXM31 on 2010-01-10
I managed to fix it by manually setting my time zone to Iceland,
even tough I live in Texas????

---

