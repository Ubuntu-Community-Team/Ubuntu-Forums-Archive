---
title: "Add keyboard modification to X startup ?"
date: 2010-05-09
forum: General Help
---

### Post by AboSamoor on 2010-05-09
I found the following  command to remap my faulty 'g' key to some special function key available in thinkpad R61 keyboard.

xmodmap -e "keycode 167 = g G Arabic_lam 8"

May you help me to add it run on X startup ? Also if anyone knows how can I apply such modification to the tty, that would be appreciated :).

---

### Post by dcstar on 2010-05-10
> **AboSamoor said:**
> I found the following  command to remap my faulty 'g' key to some special function key available in thinkpad R61 keyboard.

xmodmap -e "keycode 167 = g G Arabic_lam 8"

May you help me to add it run on X startup ? Also if anyone knows how can I apply such modification to the tty, that would be appreciated :).

/etc/rc.local

---

### Post by AboSamoor on 2010-05-18
It did not work in my case even I made sure that rc.local file has execution permissions.

---

