---
title: "Backslash button on the keyboard generates a different character"
date: 2011-11-05
forum: General Help
---

### Post by Simple Manager on 2011-11-05
I have a HP G62 laptop and when I'm on Ubuntu, I am unable to write a backslash because the button generates a different character ( <> ).

Tried to change the keyboard layout ( language ) and the keyboard model itself but the problem persists.

What can I do to get all my keyboard buttons in place ?

---

### Post by hwttdz on 2011-11-05
I'd look into xkeycaps:
[http://www.jwz.org/xkeycaps/](http://www.jwz.org/xkeycaps/)
It's also in the repo, find the closest match with respect to physical layout, then edit the keys you need to, click "write map" or something which will generate a modified keyboard layout file, and then add a line which parses the keyboard layout to one of your login scripts.

---

