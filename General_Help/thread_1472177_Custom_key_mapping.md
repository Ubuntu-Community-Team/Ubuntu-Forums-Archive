---
title: "Custom key mapping"
date: 2010-05-04
forum: General Help
---

### Post by vinnarkillen on 2010-05-04
Whats the easiest way to map F10 F11 F12 so that they print å ä ö and Å Ä Ö when using Shift?:popcorn:
Using Ubuntu 10.04.

---

### Post by vinnarkillen on 2010-05-09
cat ~/.xmodmaprc

keycode  133 = U00e5 U00c5
keycode  135 = U00e4 U00c4
keycode  105 = U00f6 U00d6

where keycodes caught using xev, in this case left win-key (133), right win-context-key (135) and right-ctrl (105). First unicode following = is result without Shift and the second with Shift. F10-F12 didn't work togheter with Shift for some reason.

---

