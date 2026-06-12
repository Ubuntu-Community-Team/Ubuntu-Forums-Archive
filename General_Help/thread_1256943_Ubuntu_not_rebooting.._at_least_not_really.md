---
title: "Ubuntu not rebooting.. at least not really"
date: 2009-09-03
forum: General Help
---

### Post by P4man on 2009-09-03
Hi,

Since a few days, when I restart ubuntu, it doesnt reboot all the way. I get the usplash thing going backwards to the point where Id expect  it to reboot and having screen flickering before getting a bios screen, but well before that,  without bios or grub screen, it starts booting ubuntu again?

In a way this is really neat, its a really fast reboot if I would need to boot ubuntu again, but sometimes, I need to boot something else :) so any clues whats going on ?

I checked my logs, but saw nothing strange there.

Shutting down works fine btw

---

### Post by P4man on 2009-09-05
*bump*

---

### Post by NoaHall on 2009-09-05
Maybe you're just restarting x server.
"Alt + K + PrintScreen" (used to be "ctrl + alt + backspace")

---

### Post by P4man on 2009-09-05
no, it goes way further then just restarting X. The "progress bar" goes back almost to zero, if i disable splash I see it kill everything, not just X.

---

