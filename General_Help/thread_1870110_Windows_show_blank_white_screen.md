---
title: "Windows show blank white screen"
date: 2011-10-26
forum: General Help
---

### Post by crutch145 on 2011-10-26
Anytime I open a window, e.g. Ubuntu Software Center, Google Chrome, etc.  All I see if a blank white screen.  In the case of Google Chrome and Firefox, if I double click the bar at the top to make the window smaller, it shows the contents of the window.  But this does not work for the Ubuntu Software Center... it just stays white for an indefinite period of time.  I have rebooted, and still get the same thing.  Any ideas? 

Thanks,

Justin

---

### Post by matt_symes on 2011-10-26
Hi

Is it a refresh issue ?

With windows obscured (white), press ALT and F2 and the same time and type

```
xrefresh -white
```

If that does not work then try it from a terminal. When the window is redrawn does it show the window correctly ?

Kind regards

---

### Post by crutch145 on 2011-10-29
After following your instructions, it did not work instantly.  But after rebooting, the problem has not re-appeared since.  Thanks, Matt!

Justin

---

