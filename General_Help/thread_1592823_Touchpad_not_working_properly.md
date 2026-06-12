---
title: "Touchpad not working properly"
date: 2010-10-11
forum: General Help
---

### Post by Prominence on 2010-10-11
upon the upgrade from 10.04 to 10.10, all upgraded nicely, except for my touchpad, which can't right click anymore, I can use the scroll on the side, and the button-trackpad just functions as a left click. 

I have an HP Pavilion dv6, with a touchpad like that of the HP Envy, click touchpad, with depressing ends on the bottom and middle respectively for left, middle, and right click.

I submitted a bug report on this when it was in beta, is there a solution to this issue? I use my laptop for work, so I would appreciate a fix... or something I could do aside from uninstalling my Operating System and reinstalling the previous version, which would seem to be a hassle.

Any and all help is appreciated.

Danke.

---

### Post by Prominence on 2010-10-12
bump

---

### Post by Prominence on 2010-10-12
anyone...?

---

### Post by rahul_lav on 2012-08-02
echo "options psmouse proto=imps"|sudo tee -a /etc/modprobe.d/psmouse.conf; sudo modprobe -r psmouse; sudo modprobe psmouse

works for me

---

### Post by wildmanne39 on 2012-08-02
Hi, this is an old thread so it has been closed, please do not post in threads that have not had a post in a year or more, thanks for sharing.

---

