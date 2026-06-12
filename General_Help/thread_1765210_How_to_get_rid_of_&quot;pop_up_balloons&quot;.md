---
title: "How to get rid of &quot;pop up balloons&quot;"
date: 2011-05-22
forum: General Help
---

### Post by zadok1 on 2011-05-22
One of the things I HATE about Windows is the infernal "pop up balloons" which tell you everything over and over again until you want to chuck the damn thing through the "window".

Pop-up balloons are OK when they tell you something useful, but when a big ugly black box pops up and tells you for the 100,000th time that you are "disconnected from the Internet" after re-starting the system from suspend mode, it gets a little tedious.

Here's how I got rid of this thing. You can restore it using this method, in case you find it useful in any way.

Open a terminal, and type:

sudo mv /usr/lib/notify-osd .

The . at the end tells it to move the notification program to the current directory, which will probably be your home directory. You can put it anywhere, and move it back again should you wish.

You will need to restart your system for this change to take effect.

Zadok1.

---

