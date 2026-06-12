---
title: "Command Line back into X (GUI Desktop)?"
date: 2006-04-11
forum: General Help
---

### Post by jms830 on 2006-04-11
I know that if I type startx from the command line, it will get me to my desktop GUI, but how can I get back in if X is already running, for instance if I hit ctrl+alt+backspace? I have just been "sudo killall gdm" and then startx or something of the like, but then I lose everything and have to log back in. So... basically whats the command to get out of the command line and back in my current GUI desktop?

---

### Post by lotheac on 2006-04-11
If you kill GDM, X won't be running. If you kill X using ctrl+alt+backspace, you are going to lose whatever you were working on that wasn't saved.

But if X *is* running and you've switched to a console with say, ctrl+alt+f1, you can switch back to X with alt+f7.

---

### Post by jms830 on 2006-04-11
Ah, yes thank you, I had used ctrl+alt+f1 and couldn't get back.

---

### Post by jms830 on 2006-04-11
weird, when I do this on my laptop, it doesn't bring me back to the desktop (with ctrl+alt+f7) but rather makes my sceen look like an acid trip with colors leaking all over the place.

---

### Post by Blarion on 2006-04-11
[QUOTE=jms830]weird, when I do this on my laptop, it doesn't bring me back to the desktop (with ctrl+alt+f7) but rather makes my sceen look like an acid trip with colors leaking all over the place.[/QUOTE]
Hrm, that seems werid. What kind of video card do you have, and what driver?

---

### Post by jdong on 2006-04-11
[QUOTE=jms830]weird, when I do this on my laptop, it doesn't bring me back to the desktop (with ctrl+alt+f7) but rather makes my sceen look like an acid trip with colors leaking all over the place.[/QUOTE]
That is pretty classic video corruption. Caused by a combination of buggy graphics drivers and buggy graphics hardware.

---

