---
title: "Bring back Terminal Menu Bar"
date: 2009-08-30
forum: General Help
---

### Post by kkrishnan on 2009-08-30
While trying to embed my terminal into the desktop, I permanently removed the menu bar from my terminal (I unticked "show by default" in the general tab in profile preferences) and now I can't bring it back.

Any ideas?

---

### Post by scouser73 on 2009-08-30
[[COLOR="Red"]**http://ubuntuforums.org/showthread.php?t=1000385**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1000385")

---

### Post by geirha on 2009-08-30
Hit Alt+F2 and run «gconf-editor». Browse to /apps/gnome-terminal/profiles/Default, then toggle the checkbox on «default_show_menubar».

---

### Post by kkrishnan on 2009-08-30
Sorry, may be I state the problem clearly.  I upped the transparency on the terminal window to full and then permanently deleted the menu bar of the terminal.

Now, I desperately need:
1. The Menu Bar
2. No transparency

because I can't read a thing now.

---

### Post by kkrishnan on 2009-08-30
Thanks so much!! It worked.

---

