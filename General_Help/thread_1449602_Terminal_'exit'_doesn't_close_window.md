---
title: "Terminal 'exit' doesn't close window"
date: 2010-04-08
forum: General Help
---

### Post by SoftwareExplorer on 2010-04-08
Hi. When I type exit in a gnome-terminal, the prompt disappears but the window does not close. I had this problem with Karmic. I ignored it. Eventually, I installed lucid and only copied over my my /home to the new lucid partition. Therefore, I think it is a setting of mine. Where do I start looking to try to fix this?

---

### Post by Kevbert on 2010-04-08
Have you tried in terminal going to Edit-Profile Preferences and checking there ? (see attached). Also try pressing Alt-F2 and in 'Run Application'' enter 'gconf-editor' and click on 'Run'. Now go to /apps/gnome-terminal/global and check your settings there (if you click on each name on the right it gives a description of the action). Also check /apps/gnome-terminal/profiles/Default/exit action is marked close (you can change this with a right mouse click and select 'Edit key').

---

### Post by SoftwareExplorer on 2010-04-08
> **Kevbert said:**
> Have you tried in terminal going to Edit-Profile Preferences and checking there ? (see attached). Also try pressing Alt-F2 and in 'Run Application'' enter 'gconf-editor' and click on 'Run'. Now go to /apps/gnome-terminal/global and check your settings there (if you click on each name on the right it gives a description of the action). Also check /apps/gnome-terminal/profiles/Default/exit action is marked close (you can change this with a right mouse click and select 'Edit key').

Thanks! I had to set my profile preferences for 'When a command exits' to 'Exit the terminal' instead of 'Hold the terminal open'.

---

### Post by Rajan_92 on 2010-06-16
Thanks solved my problem too......

---

### Post by Csirkefogo on 2011-03-14
I had the same "problem". It is now solved :)

---

