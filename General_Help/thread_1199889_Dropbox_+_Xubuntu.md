---
title: "Dropbox + Xubuntu??"
date: 2009-06-29
forum: General Help
---

### Post by pointyblue on 2009-06-29
I'm running Xubuntu 904 on my netbook, need to install Dropbox.

While it appears to install without problems I can't use it as it requires Nautilus to run. :-k

How on earth do I work around this problem - I really need to make Dropbox work?

:confused:

---

### Post by pointyblue on 2009-06-30
Anyone..?

---

### Post by Redsandro on 2009-11-06
I have installed DropBox and it starts nautilus. Now when I start, the desktop goes:

*blank -> thunar -> nautilus -> thunar*.

I think nautilus is only a dependency because of the updatable icons (loading, loaded etc.) and is not necessary for core function.
How can I stop nautilus from loading without removing it?

It is not in
**/etc/xdg/autostart**
or
**~/.config/autostart**

---

### Post by MattM11 on 2009-11-07
> I have installed DropBox and it starts nautilus. Now when I start, the desktop goes:

*blank -> thunar -> nautilus -> thunar*.Go to Applications > Settings > Session and Start-up

Under the Session tab you should see a list of all the applications running - including nautilus. Under "Restart Style" it should say "if running" - click that and select "never". Then (while nautilus is highlighted) click "Quit Program" followed by "Save Session". 

This should close down nautilus and prevent it running at start up.

---

