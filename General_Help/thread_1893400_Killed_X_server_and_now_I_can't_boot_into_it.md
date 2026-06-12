---
title: "Killed X server and now I can't boot into it"
date: 2011-12-10
forum: General Help
---

### Post by Dingbats on 2011-12-10
I pressed alt-printscr-K to kill X, which took me to a black screen with white text from where I had to force shutdown the computer.

Now when I turn it on, the Xubuntu login screen sometimes quickly flashes by (sometimes it won't even show), only to leave me to a black screen with white text that says "Starting" and "Stopping" this and that, with [ OK ] on the right hand side, except for "Stopping automatic crash report generation", which displays [fail] in red text.  The cursor is blinking and I can't do anything.

What do I do to start X and log in?

---

### Post by Dingbats on 2011-12-10
**** this, I'm reinstalling.

---

### Post by gennatolls on 2011-12-10
> **Dingbats said:**
> I pressed alt-printscr-K to kill X, which took me to a black screen with white text from where I had to force shutdown the computer.

Now when I turn it on, the Xubuntu login screen sometimes quickly flashes by (sometimes it won't even show), only to leave me to a black screen with white text that says "Starting" and "Stopping" this and that, with [ OK ] on the right hand side, except for "Stopping automatic crash report generation", which displays [fail] in red text.  The cursor is blinking and I can't do anything.

What do I do to start X and log in?

That is the system console, Can you press CTRL+ALT+F1 to pull up a shell login? If so you could login and enter startx to start the gui.

---

