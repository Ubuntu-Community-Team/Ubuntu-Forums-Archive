---
title: "Number pad not working after login"
date: 2010-09-04
forum: General Help
---

### Post by iamsickofschool on 2010-09-04
I can't think of what would cause this problem. The num lock light is on and I can sign in with the number pad (password is all numbers) but when I get into Ubuntu the number pad stops working with numlock light on or off. What could cause this?

---

### Post by dcstar on 2010-09-04
> **iamsickofschool said:**
> I can't think of what would cause this problem. The num lock light is on and I can sign in with the number pad (password is all numbers) but when I get into Ubuntu the number pad stops working with numlock light on or off. What could cause this?

Incorrect keyboard type detected.

System-Preferences-Keyboard-Layouts-Keyboard model

---

### Post by abouwens on 2010-10-08
I was having the same problem, however, the keyboard type was fine. This solved it for me:
[LIST]
[*]System -> Preferences -> Assistive technologies
[*]click "keyboard accessibility"
[*]go to the tab "mouse keys"
[*]uncheck "pointer can be controlled using keypad"
[/LIST]

---

### Post by viking_pl on 2010-11-16
Thank you iamsickofschool. This is not an expected behaviour of keyboard-mouse tool. Did one of you report this as a bug already. I don't want to double the report. If you did can you post a link to the bug?

---

### Post by IndyGunFreak on 2010-12-05
> **viking_pl said:**
> Thank you iamsickofschool. This is not an expected behaviour of keyboard-mouse tool. Did one of you report this as a bug already. I don't want to double the report. If you did can you post a link to the bug?

I don't think they view it as a bug, more a "feature".... Gotta be the dumbest thing I've ever heard of.

---

### Post by PyrexKidd on 2011-11-30
Hey, I know it's a year late, but hopefully this will help someone else, try shift + numlock if your numpad stops working, also, the above techniques work in gnome pre Gnome3.

---

