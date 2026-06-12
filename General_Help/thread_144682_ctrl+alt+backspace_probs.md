---
title: "ctrl+alt+backspace probs"
date: 2006-03-14
forum: General Help
---

### Post by sjoseph on 2006-03-14
i recently discovered that ctrl+alt+backspace restarts GNOME without restarting the computer. it's a great find for beginners. the question is while it worked a few times, it now shifts me into console mode instead. and i can't get back..any thoughts..

---

### Post by rfruth on 2006-03-14
It works for me once per boot, actually it always works but I only get Gnome (X) automatically after the 1st Ctrl-Alt-bspace after that get the command line (console) startx does the trick then though, clear as mud ?

---

### Post by jrib on 2006-03-14
'sudo /etc/init.d/gdm start' should get you back.  As I understand it, ctrl+alt+backspace just zaps X and then gdm starts it up again.  But if gdm is not running for some reason, then you just end up at a console.

---

### Post by sjoseph on 2006-03-14
thanks for the input.

---

