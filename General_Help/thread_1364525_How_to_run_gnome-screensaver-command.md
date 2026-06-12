---
title: "How to run gnome-screensaver-command"
date: 2009-12-26
forum: General Help
---

### Post by dictum9 on 2009-12-26
I want the screen to auto lock every N minutes, how do I do that with gnome-screensaver-command?

I know I can run it manually but how do I run it in the background like a daemon?

---

### Post by peakpc on 2009-12-26
I don't know if I am misunderstanding the question or not but, If you are running Ubuntu 9.10 just go to Screensaver Preferences, pick a screensaver, set the time and check the lock screen option.

---

### Post by Vaphell on 2009-12-26
as a general advice, when you don't know how to use a command in terminal, just run it with **--help** parameter, it's rather widely used by command line programs.

**gnome-screensaver-command --help**

it says there is lock option (-l, --lock) and you could add it to crontab (assuming you really want to lock the screen every 15 minutes regardless of user activity)

---

