---
title: "xterm properties in gnome (11.10)"
date: 2011-10-20
forum: General Help
---

### Post by pauln600 on 2011-10-20
Hm, seems like a lot of things that used to be accessible and obvious have become hidden... like, how to control the visual properties of xterm (font size, scroller etc.).  Can someone point me to the magic buttons?

Thanks,
Paul

---

### Post by TeoBigusGeekus on 2011-10-20
It should be in the ~/.Xdefaults file.
Here's my xterm part:
```
XTerm*background: black
XTerm*foreground: cyan
XTerm*faceName: DroidSansMonoDotted:size=11
XTerm*ScrollBar:  false
XTerm*Geometry: 104x20
```

---

### Post by gsmanners on 2011-10-20
> **TeoBigusGeekus said:**
> It should be in the ~/.Xdefaults file.
Here's my xterm part:
...

Cool. I've been using exec parameters (like -geometry for the size).

---

