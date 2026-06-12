---
title: "Can't shut down"
date: 2010-05-07
forum: General Help
---

### Post by dazcaz on 2010-05-07
I have an Acer Aspire 1650 laptop. (Intel M 735)
Often when I try and shut down the machine goes through the shut down procedure and then gives me the login screen again.
The only way to turn off the computer is to press and hold the power button.

Any ideas?

---

### Post by dracayr on 2010-05-07
what about 'sudo shutdown -h now'?
or 'sudo init 0'

---

### Post by dazcaz on 2010-05-07
"sudo shutdown -h now" works a treat.
Normally clicking the shut down tab works, but quite often it doesn't.

---

### Post by dracayr on 2010-05-07
Well I have no Idea whether the shutdown command of the window is configurable, or how to do it.. google didn't return anything either.

You could, if you want a graphical shutdown, create a launcher to a script that shuts down (You'd have to use gksudo then though).

dracayr

---

