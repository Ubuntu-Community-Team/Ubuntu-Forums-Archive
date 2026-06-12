---
title: "nvidia-settings not remembering twinview between reboots. Maybe because of tmpfs?"
date: 2011-03-02
forum: General Help
---

### Post by LonelyStar on 2011-03-02
Hi,

I have 2 monitors and enabled twinview using nvidia-settings. But this setting is not remembered between reboots. I remember that to be different. What could be the reason?
Could it be, because I am using tmpfs and it therefore /tmp is emptied between reboots?
How can I fix this?

Thanks!
Nathan

---

### Post by wojox on 2011-03-02
Are you setting them at root?

```
gksudo nvidia-settings
```

---

### Post by LonelyStar on 2011-03-02
Hey,

I did not. But now I did, but it does no make a difference.

---

### Post by wojox on 2011-03-02
Did you save the config to xorg.conf?

tmpfs has nothing to do with your nvidia-settings. xorg.conf is stored in /etc/X11/xorg.conf.

---

### Post by LonelyStar on 2011-03-02
That was the problem, it works now, thanks!

---

