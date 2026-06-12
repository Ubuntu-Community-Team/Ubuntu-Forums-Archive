---
title: "Keyboard Maping for a 111 key keboard ?"
date: 2010-03-03
forum: General Help
---

### Post by wwsoft on 2010-03-03
Hello ,  I have an 111 key keyboard. It has several extra keys that are unrecognised by Ubuntu's generic keyboard layouts. How can I get Ubuntu to recognize it ? [since I'm a programmer and would like some use out of the extra keys ! ]

---

### Post by tgalati4 on 2010-03-03
What's the make and model of the keyboard?

Open a terminal, run xev.

Push each extra key and watch the terminal for the keycodes.

Make a .Xmodmap file in your home directory with the appropriate settings.

[http://ubuntuforums.org/showthread.php?t=653124&highlight=keyboard+xmodmap](http://ubuntuforums.org/showthread.php?t=653124&highlight=keyboard+xmodmap)

---

### Post by wwsoft on 2010-03-03
> **tgalati4 said:**
> What's the make and model of the keyboard?

Open a terminal, run xev.

Push each extra key and watch the terminal for the keycodes.

Make a .Xmodmap file in your home directory with the appropriate settings.

[http://ubuntuforums.org/showthread.php?t=653124&highlight=keyboard+xmodmap](http://ubuntuforums.org/showthread.php?t=653124&highlight=keyboard+xmodmap)

it does not appear to register ... however Im running the mapping for a generic 103 key keyboard

---

