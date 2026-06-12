---
title: "Hangs on Shutdown"
date: 2010-01-13
forum: General Help
---

### Post by NiGhtMarEs0nWax on 2010-01-13
Hi,

Every time i shut-down my system it hangs indefinitely.

The screen goes blank immediately as soon as i shut down and it just sits there, blank screen.

Is there anyway to log the shut-down process to give you guys a more detailed insight?
is this a known issue?


Ubuntu Karmic 9.10

---

### Post by NiGhtMarEs0nWax on 2010-01-14
bump

---

### Post by NiGhtMarEs0nWax on 2010-01-14
bump, i really need to get this sorted.

---

### Post by NiGhtMarEs0nWax on 2010-01-15
noone can help me on this?

Thanks.

---

### Post by Barriehie on 2010-01-15
Although my machine doesn't hang on shutdown just 2 days ago I did a clean reinstall and it was taking a LONG time to shutdown.  I ended up going into System > Administartion > Login Window > Edit Commands and edited the shutdown to look like this:
```

/sbin/shutdown -P now "Shut Down via gdm."
```
Now it's pretty quick, done in seconds.

No guarantee's though!  What does your machine do if you:
```

sudo shutdown -P now
```
from a terminal?

---

### Post by NiGhtMarEs0nWax on 2010-01-15
Thanks for the reply!

Same thing, it just hangs.

is there any way i can log the shutdown process?


Thanks.

---

### Post by Barriehie on 2010-01-15
> **NiGhtMarEs0nWax said:**
> Thanks for the reply!

Same thing, it just hangs.

is there any way i can log the shutdown process?


Thanks.

Not that I'm aware of, mine seems to come and go.

---

### Post by NiGhtMarEs0nWax on 2010-01-16
Thanks for the reply!

it appears it was a shellscript that was running at system halt/reboot, it was also causing problems elsewhere on my system. so i've just decided to remove it and find an alternative.


Thanks!

---

