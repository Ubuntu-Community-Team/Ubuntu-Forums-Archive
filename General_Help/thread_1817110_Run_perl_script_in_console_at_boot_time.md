---
title: "Run perl script in console at boot time"
date: 2011-08-02
forum: General Help
---

### Post by jmumby on 2011-08-02
I have the following command in my rc.local file. 

```
xterm -e perl /home/user/email2sms.pl
```

If I run rc.local from nautilus it works as expected. However when I boot nothing happens. I would like a console to popup and show the activity of the perl script. 

Thx

---

### Post by Beacon11 on 2011-08-03
> **jmumby said:**
> If I run rc.local from nautilus it works as expected. However when I boot nothing happens. I would like a console to popup and show the activity of the perl script.

Yeah, you have that in the wrong spot. rc.local is run ON BOOT, and you want something to run on graphical login (at least, that's how it sounds). To do that, check out Startup Applications (if using Gnome, System > Preferences > Startup Applications), and add your xterm line in there like ```
/usr/bin/xterm -e perl /home/user/email2sms.pl
```

---

### Post by Hatsune Miku on 2011-08-03
> **jmumby said:**
> I have the following command in my rc.local file. 

```
xterm -e perl /home/user/email2sms.pl
```

If I run rc.local from nautilus it works as expected. However when I boot nothing happens. I would like a console to popup and show the activity of the perl script. 

Thx

Whats your Desktop Environment/Windows Manager?

---

### Post by jmumby on 2011-08-05
> **Beacon11 said:**
> Yeah, you have that in the wrong spot. rc.local is run ON BOOT, and you want something to run on graphical login (at least, that's how it sounds). To do that, check out Startup Applications (if using Gnome, System > Preferences > Startup Applications), and add your xterm line in there like ```
/usr/bin/xterm -e perl /home/user/email2sms.pl
```

PERFECT! thank you very much.

---

### Post by Beacon11 on 2011-08-05
> **jmumby said:**
> PERFECT! thank you very much.

My pleasure!

---

