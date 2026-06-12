---
title: "yakuake startup?"
date: 2009-10-17
forum: General Help
---

### Post by PHaLaNX on 2009-10-17
I've added yakuake to /.kde/Autostart folder to run it at startup, but when it runs it automatically drops down the console without pressing the f12 key, is there any way to prevent this?

---

### Post by PHaLaNX on 2009-10-20
Is it the case with anyone using yakuake? Any ideas?

---

### Post by tomas.splatch on 2010-01-11
Had the same problem, this helps:

Yakuake opens its window when it is run again while it is already running. Most
likely you see the window opening because Yakuake is started twice after login
on your system: Once by KDE's Session Manager, which restarts all apps that
were running at logout by default (see System Settings -> Advanced -> Session
Manager), and once by your Autostart entry.

Found [here]("http://www.kde-apps.org/content/show.php?content=29153")

---

### Post by dotpc on 2013-03-12
Thanks so much, just fixed the same problem on Chakra Linux (KDE 4.10.1). Cheers!

---

### Post by lisati on 2013-03-13
Thank you for your feedback. It's good to know that a solution from two years ago is still uesful, even though a lot can change in that time.

Old thread closed.

---

