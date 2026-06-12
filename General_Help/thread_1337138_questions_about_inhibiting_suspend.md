---
title: "questions about inhibiting suspend"
date: 2009-11-25
forum: General Help
---

### Post by Andreas1 on 2009-11-25
1: i noticed that my system goes to suspend even while copying files in nautilus or burning cds. aren't those actions supposed to inhibit suspend, since they break if they are interrupted?

2: is there a command to temporarily inhibit suspend, as can be done with the inhibit panel applet? the one i tried was ```
gnome-screensaver-command -i
``` but this does not prevent suspend if i manually lock the screen afterwards. (panel applet does work, but i find it a bit ridiculous to need an applet for such a simple task)

i should add that such issues come up because i have set my power management timeouts to extremely low values, like 3 min before suspend kicks in.

---

### Post by Andreas1 on 2009-11-26
bump

---

### Post by wilee-nilee on 2009-11-26
I am curious as to why you have the suspend set at 3 min.

---

### Post by Andreas1 on 2009-11-26
> **wilee-nilee said:**
> I am curious as to why you have the suspend set at 3 min.

experience: the longest task you can do at the computer without any interaction is reading one screen full of text, and that takes less than 3 minutes. so if there is no interaction for 3 minutes it is safe to assume i am not at the computer any more.

honestly i don't understand why some people have their computer running all the long just in case they might it it hours later.

anyway, the problems i described could also come up with longer timeouts, however less likely of course, but still...

---

### Post by wilee-nilee on 2009-11-26
> **Andreas1 said:**
> experience: the longest task you can do at the computer without any interaction is reading one screen full of text, and that takes less than 3 minutes. so if there is no interaction for 3 minutes it is safe to assume i am not at the computer any more.

honestly i don't understand why some people have their computer running all the long just in case they might it it hours later.

anyway, the problems i described could also come up with longer timeouts, however less likely of course, but still...

That is a logical reason I use a net book and just shut it off when not in use, it was cheap so it will wear out at some point. I don't know any scripts to achieve the task you want but there probably is one. It seems counter intuitive to not make a couple of clicks to change the suspend if your going to be using to burn or print.

---

