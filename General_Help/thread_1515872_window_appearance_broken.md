---
title: "window appearance broken"
date: 2010-06-23
forum: General Help
---

### Post by M!K3_$ on 2010-06-23
My window content is really grey and boxy. But the title bars and what not are fine. When I change my theme it doesn't fix it.
See screenshot for example

---

### Post by drpjkurian on 2010-06-23
Hi
You can install new themes. icons etc.
Or you can even customise your window border and title bars

---

### Post by M!K3_$ on 2010-06-23
Yeah. i tried that. the window borders titles and icons work. nothing else does.

You can see this in my screenshot.

---

### Post by drpjkurian on 2010-06-23
> nothing else does.



Hi What do you mean by that???

---

### Post by petellgra on 2010-06-23
Hi
That happens to me whenever I open the downloads folder and the window goes grey and freezes. Now I don't use that folder. I'll watch your thread to see if you get an answer. Also mine went grey when I used Inkscape. The only two times. 
Pete

---

### Post by wilee-nilee on 2010-06-23
Looks like low graphics mode have you checked system-admin-hardware drivers to see if anything is there.

Run in the terminal.
```
lspci | grep VGA
```

---

### Post by warfacegod on 2010-06-23
That looks like you are browsing your computer files as root or logging in as root. If that's what you are doing then you should stop immediately. Browsing as root can be very dangerous to your system and should only be done when necessary.

---

### Post by M!K3_$ on 2010-06-23
> **wilee-nilee said:**
> Looks like low graphics mode have you checked system-admin-hardware drivers to see if anything is there.

Run in the terminal.
```
lspci | grep VGA
```

mike@jester:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

---

### Post by M!K3_$ on 2010-06-23
> **warfacegod said:**
> That looks like you are browsing your computer files as root or logging in as root. If that's what you are doing then you should stop immediately. Browsing as root can be very dangerous to your system and should only be done when necessary.

*shrug*
I log in as myself (mike). And I still need to elevate myself to do administrative tasks, etc.

Is there another way to check this?

---

### Post by M!K3_$ on 2010-06-23
> **drpjkurian said:**
> Hi What do you mean by that???


If you look at the above posted screenshot you will see that all the "stuff" inside my windows is all grey and boxy. But everything else is fine (window boarders, etc.).

---

### Post by M!K3_$ on 2010-06-23
It all happened after I compiled the GTK+ source from [http://www.gtk.org/]("http://www.gtk.org/")

---

### Post by macstar on 2010-06-23
try to completely remove nautilus and reinstall nautilus in the synaptic package manager.

---

### Post by M!K3_$ on 2010-06-23
Just tried Nautilus. Didn't work.

It's more than just nautilus though, its everything. 

thank you all for your help so far.

---

