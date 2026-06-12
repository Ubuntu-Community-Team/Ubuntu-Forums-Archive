---
title: "tty display dims after 10 minutes"
date: 2009-08-14
forum: General Help
---

### Post by DMcA on 2009-08-14
While using virtual text terminal the display will dim after 10 minutes of inactivity (i.e. no key presses, on screen changes do not prevent this). Some text is just about readable still, so I assume the backlight is just being turned off. I'm using a laptop but this happens when plugged in so it can't be a power-saving feature. In gnome I have "put display to sleep" set to never. 

Is there a way to disable this from occurring?

---

### Post by DMcA on 2009-08-18
For anyone interested the following command appears to work: 

```
setterm -blank 0 -powersave off -powerdown 0
```

(I haven't investigated which switch is responsible). It's rather difficult to google this without knowing setterm is necessary but using that in a search gives plenty of information.

---

