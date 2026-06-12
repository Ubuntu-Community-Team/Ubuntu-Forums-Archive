---
title: "Terminal font"
date: 2012-08-17
forum: General Help
---

### Post by Odexios on 2012-08-17
Hello everyone!

I'm writing a little game in C, and I'm using ncurses as a library to write the interface. I tested it on the tty, and everything went smooth; today I tried it on LXTerminal and some characters were, well, really ugly. I'm not sure it's a font problem, but that's what I thought it could be.

Anyway, for instance, when in the tty a character is printed like this:

&#8594;

in LXTerminal the same charater is printed like this:

>

and so on (&#8595; - V, &#8593; - ^, &#8592; - <). I'd have guessed that a terminal would have had nicer characters than the tty, but I guess I was wrong. Is there any way I can "fix" this, so that the terminal shows the same nice characters of the tty?

I understand it's a an unimportant issue, but appearences count, too.

---

### Post by marinara on 2012-08-19
probably ncurses doesn't recognise the terminal type in lxterminal, force it.

---

### Post by Odexios on 2012-08-23
Any hint in how to do it? My google-fu must be rusty, I'm having a hard time finding a solution.

---

