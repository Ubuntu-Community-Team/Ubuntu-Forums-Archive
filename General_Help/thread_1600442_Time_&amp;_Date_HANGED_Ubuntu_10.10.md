---
title: "Time &amp; Date HANGED Ubuntu 10.10"
date: 2010-10-19
forum: General Help
---

### Post by electrosam on 2010-10-19
Hello !
The Time and Date at the top docking bar is Hanged.
It shows Mon, Oct 18, 6:35 PM. That's all.
But when I click on it, it shows correct date in Calender.
And correct time in the bottom.
I believe those gadgets are not updating at all.
Cause my Battery indicator is also not working.
Please help me out.

---

### Post by sikander3786 on 2010-10-19
Did you try removing the applet from panel and then adding it back? You can also try

```
killall gnome-panel
```

to refresh the panel and see if it updates itself.

---

### Post by electrosam on 2010-10-19
Hey, that kill command worked.
Clock is working fine now.
But still having issue with Battery meter.
It shows (estinmating) when I click on it, where it should show % battery remaining.
It was working fine with ubuntu 10.04.
Please help me out.
Thanks.

> **sikander3786 said:**
> Did you try removing the applet from panel and then adding it back? You can also try

```
killall gnome-panel
```to refresh the panel and see if it updates itself.

---

