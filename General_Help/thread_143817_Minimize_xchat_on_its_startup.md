---
title: "Minimize xchat on its startup"
date: 2006-03-13
forum: General Help
---

### Post by MblKiTA on 2006-03-13
Is there is a way to minimize xchat on its startup? I'm using xchat-systray. It perfectly minimizes it to tray. But can I do this automatically?

---

### Post by frodon on 2006-03-13
Yes, thanks to devil's Pie : [http://doc.gwos.org/index.php/Automating_gnome](http://doc.gwos.org/index.php/Automating_gnome)

---

### Post by MblKiTA on 2006-10-18
And how can I do this in kubuntu?

---

### Post by frecon on 2008-05-01
> **MblKiTA said:**
> Is there is a way to minimize xchat on its startup? I'm using xchat-systray. It perfectly minimizes it to tray. But can I do this automatically?

In Ubuntu 8.04 you can start xchat minimized if you run the following command in the terminal:
```
xchat --minimize=2
```

So if you want XChat to automatically startup when Ubuntu starts, just add that line into a new start program in System > Preferences > Sessions.

---

