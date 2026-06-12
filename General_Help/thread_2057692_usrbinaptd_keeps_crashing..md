---
title: "/usr/bin/aptd keeps crashing."
date: 2012-09-14
forum: General Help
---

### Post by MrWestwood on 2012-09-14
I have a fresh install of 12.04 and every time my machine boots up I get a crash error. The crashed program is always /usr/bin/aptd. The error now also seems to extend to a distribution upgrade. Ubuntu keeps saying something along the lines of the system could not be upgraded. I haven't tried to upgrade the system. 

I'm not with the machine currently but I can provide screenshots and any details needed.

---

### Post by MrWestwood on 2012-09-14
Anyone.

---

### Post by Lars Noodén on 2012-09-14
It will help if you can post the exact error message verbatim.  Also, if there is anything relevant in /var/log/syslog post the relevant excerpt.

---

### Post by MrWestwood on 2012-09-14
Will do.

---

### Post by SlugSlug on 2012-09-14
can you use apt?

```
sudo apt-get install aptitude
```

```
sudo aptitude reinstall apt
```

---

### Post by MrWestwood on 2012-09-15
The only sort of error report I can get fromthis is the GUI crash report.

[IMG]http://i.imgur.com/CIjK4.png[/IMG]

Slug, your suggestion didn't work. It just brought back the error in performing distribution upgrade message.

---

### Post by SlugSlug on 2012-09-15
```
sudo aptitude reinstall aptdaemon
```

---

### Post by MrWestwood on 2012-09-15
> **SlugSlug said:**
> ```
sudo aptitude reinstall aptdaemon
```


Still same.

[IMG]http://i.imgur.com/D1siO.png[/IMG]

---

### Post by Lars Noodén on 2012-09-15
Is there anything in /var/log/syslog related to the crashes?

---

### Post by MrWestwood on 2012-09-15
> **Lars Noodén said:**
> Is there anything in /var/log/syslog related to the crashes?

The only thing I can see is this.

Sep 15 11:45:34 Westwood gnome-session[1440]: WARNING: Failed to start app: Unable to start application: Failed to execute child process "nm-applet" (No such file or directory)

---

