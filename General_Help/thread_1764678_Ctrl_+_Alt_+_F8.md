---
title: "Ctrl + Alt + F8"
date: 2011-05-22
forum: General Help
---

### Post by Curse on 2011-05-22
I've just recently learned about the hotkeys CTRL+ALT+F1-6, which (afaik) are terminals based off of their own logins, separate from your graphical login. 

When I hit, say, CTRL+ALT+F1 after logging in from the normal startup, CTRL+ALT+F8 is what brings me back to my desktop. Is that what is intended? It seems to me that CTRL+ALT+F7 is the terminal for your current graphical login, and CTRL+ALT+F8 is what brings you back to the graphical part of that; so what about F9-12?

I have a feeling I'm not understanding something correctly.

---

### Post by Jack Brown on 2011-05-22
[http://ubuntuforums.org/showthread.php?t=833765](http://ubuntuforums.org/showthread.php?t=833765)   see the third post on that.  short and sweet.

---

### Post by Curse on 2011-05-22
Hm.. so is it dangerous to be using TTY1, for example, to install programs and do things?

From what I am getting, TTY8 is what my current X session (X session = gfx desktop session?) is running on?

EDIT: This is probably important. Since restarting the computer I've logged out, then back in. So normally I'd be in TTY7, rather than TTY8, right?

EDIT2: Also, when I go to, say, TTY9, it just gives me a blinking cursor ( _ symbol), can I do anything from here? When I type nothing shows up.

---

### Post by Jack Brown on 2011-05-22
good questions.

will wait for someone with more experience to answer.

it's  not easy to find comprehensive and reliable info on it.

can only say with a great degree of certainty that it won't be more dangerous to use tty1 as compared to the GUI ones, as you still need to log in to do stuff.  

plus you see the date and time when you last logged in.

Edit: (of course you can always experiment and research, and document your findings here)
Edit2: looks like you need to remember to logout the text ttys (?consoles) as you stay logged in if you change to the other ones and then switch back

---

### Post by 3rdalbum on 2011-05-22
> **Curse said:**
> Hm.. so is it dangerous to be using TTY1, for example, to install programs and do things?

No, not at all. They are there to be used. You can install software from TTY exactly like you'd install software from an Xterm or Gnome-Terminal.

> EDIT2: Also, when I go to, say, TTY9, it just gives me a blinking cursor ( _ symbol), can I do anything from here? When I type nothing shows up.

Yeah, there's no actual shell like Bash running on TTY9, so that's perfectly normal.

---

