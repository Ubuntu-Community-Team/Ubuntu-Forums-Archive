---
title: "Auto start tty1"
date: 2010-10-31
forum: General Help
---

### Post by Righard on 2010-10-31
Hello,
I removed gdm from my computer and want it to start tty1 on startup automatically. Does anybody know how to do this? At this point it's just blinking a cursor until I press Ctrl+Alt+F1.

Thank you!
Righard

---

### Post by Righard on 2010-10-31
I keep solving stuff minutes after asking today; sorry :)

Putting "chvt 1" in /etc/rc.local solved my problem.

Thx anyway!

---

### Post by dcstar on 2010-11-01
> **Righard said:**
> I keep solving stuff minutes after asking today; sorry :)

Putting "chvt 1" in /etc/rc.local solved my problem.

Thx anyway!

So it is Solved then? (read below)

---

### Post by Righard on 2010-11-01
I did mark this thread solved?

---

### Post by ovidiu_b13 on 2011-07-26
This worked for me to on Ubuntu 10.10. X11 and gnome still loads on tty7, but you can start working in tty1 almost 10-15 seconds earlier. Thanks!!!:KS

Don't forget to put "chvt 1" before "exit 0".

---

