---
title: "Can't return to Ubuntu's regular desktop"
date: 2010-12-11
forum: General Help
---

### Post by blakjakd on 2010-12-11
I have Ubuntu 10.10 and turned it on after enabling my nvidia video card, but instead of opening regularly, it went to a black screen that said the following.
[I]
Ubuntu 10.10 Inspiron8200 ttyl

Inspiron8200 login:

[/I]
I can login but this is only like the terminal (or maybe like the recovery console?) (I can only type and receive text)
How do I start Ubuntu like normal?

thanks

---

### Post by Foxheadz on 2010-12-11
not sure about booting normaly but from that screen you can return to it by typing

your username
then your password
then "startx" (without quotations)

---

### Post by MrKphat on 2010-12-11
You click  ctrl+alt+F7 to go back to normal desktop...

Usually people go to this terminal when something weird happened on an install (particularly with graphics cards).
If the above did not work...

1. type in your username
2. type in your password
3. try these:
```
sudo apt-get update
``````
sudo apt-get upgrade
```then try clicking ctrl+alt+F7 again

---

