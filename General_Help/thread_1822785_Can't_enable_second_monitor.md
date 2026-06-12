---
title: "Can't enable second monitor"
date: 2011-08-11
forum: General Help
---

### Post by Roganartu on 2011-08-11
Hi,

I'm trying to enable my second monitor after upgrading from 10.04 to 11.04. In the process of upgrading, I had to delete my xorg.conf file because it was causing errors and preventing the desktop from displaying.

So I tried using gksu nvidia-settings to enable the second monitor. If I enable it in TwinView, nvidia settings can apply it, it shows up but I can't use it.

If I try to enable it as a separate X-screen (which is what I had in 10.04) nvidia settings is unable to apply the settings, and so I have to save it as an xorg.conf file, which then causes my desktop to no longer display.

I currently have no idea how to enable the second monitor any other way. Is there some new settings file I should know about?

Cheers,
Tony.

---

### Post by Roganartu on 2011-08-11
Found that if you place your xorg.conf file in the following folder, it seems to work correctly:

```
/usr/share/X11/xorg.conf.d
```

Weird thing is, now on the bottom monitor it displays an x for the cursor instead of the normal cursor that's displayed on the top monitor.

---

