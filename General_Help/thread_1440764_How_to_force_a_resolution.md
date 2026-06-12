---
title: "How to force a resolution?"
date: 2010-03-27
forum: General Help
---

### Post by Satchmo2 on 2010-03-27
So my monitor (a 19" acer) has a native res of 1440x900, which is not detected in display settings. How do I force the resolution to that? Please walk me through it gently as I'm kind of a linux noob.

---

### Post by munchen800 on 2010-03-27
Try typing

xrandr

into terminal it will show you supported video modes if your res. is supported it will show up

then type

xrandr --output (what ever output it uses prol VGA) --mode (screen res in format like 800x600)

example 

xrandr --output VGA --mode 1280x1024

---

### Post by Dayofswords on 2010-03-27
> **Satchmo2 said:**
> So my monitor (a 19" acer) has a native res of 1440x900

odd number

EDIT:
it seems 8.75% of the world uses that =p
[http://marketshare.hitslink.com/report.aspx?qprid=17](http://marketshare.hitslink.com/report.aspx?qprid=17)

---

