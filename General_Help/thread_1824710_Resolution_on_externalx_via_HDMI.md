---
title: "Resolution on externalx via HDMI"
date: 2011-08-14
forum: General Help
---

### Post by evaldasp on 2011-08-14
Hello,

 I have got a problem, I've connected an external LCD to my toshiba laptop 27" HP full HD monitor via HDMI port, when I set full hd resolution it bacomes black, then I have downloaded ARandR (it uses XrandR X Resize, Rotate and Reflect Extension ) application and it looked alright, but after restart old resolution come back, how to change it permanently? I set internal monitor to off :confused::confused::confused::confused:

---

### Post by realzippy on 2011-08-14
If you hit apply it does not persist reboot?
Run
```
rm ~/.config/monitors.xml

```
before using arandr...
If still not working after reboot:

Post output from
```
xrandr -q
```

---

### Post by realzippy on 2011-08-25
gave up?

---

