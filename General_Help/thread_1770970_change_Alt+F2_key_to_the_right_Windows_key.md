---
title: "change Alt+F2 key to the right Windows key?"
date: 2011-05-29
forum: General Help
---

### Post by gyyug78fg87ogguiioioioioi on 2011-05-29
just changed the Alt+f1 the menu starter to the left windows key,
and now i want the Alt+F2 key to be the right windows key instead, how can i do this?

---

### Post by silkworm2.5 on 2011-05-29
Open the keyboard shortcuts app, and find the line saying "Show the panels "Run Application" dialogue box" and alter it as you wish :)

---

### Post by gyyug78fg87ogguiioioioioi on 2011-05-29
yeah the thing is that it dosent allows me to press the windows key nothing happens
the same with the left key also, i had to change it with this command:
> gconftool-2 --set /apps/metacity/global_keybindings/panel_main_menu --type string "Super_L"

---

### Post by gyyug78fg87ogguiioioioioi on 2011-05-30
anyone?

---

### Post by inameiname on 2011-05-30
Here, this should do it. I don't have a "Super_R" on my keyboard, but it works with "Super_L":

gconftool-2 --set /apps/metacity/global_keybindings/panel_run_dialog --type string "Super_R"


UPDATE:

Also, sometimes if you've changed it from one to the other, it may not work without first removing the previous shortcut key command first, or change it to something else beforehand. You can do this through the terminal this way, or just use the configuration editor. Your choice. For example, I use my "Super_L" key to open a terminal window, using this command:

gconftool-2 --set /apps/metacity/global_keybindings/run_command_terminal --type string "Super_L"

...and I noticed when I tested the one you wanted on it, I found I couldn't simply return it back to what I prefer without first changing the 'panel_run_dialog' back to <Alt>F2

---

### Post by gyyug78fg87ogguiioioioioi on 2011-05-30
but i want the Alt+F2 key (Run Program) to be Super_R not "panel_run_dialog" :confused:
i have already that one as my Super_L, i want the Right "windows key" on my keyboard to open "Run Program" if u understand?

---

### Post by gyyug78fg87ogguiioioioioi on 2011-05-30
bump again, sorry

---

### Post by gyyug78fg87ogguiioioioioi on 2011-05-30
nobody? bump

---

### Post by gyyug78fg87ogguiioioioioi on 2011-05-30
Bump..... :|

---

### Post by inameiname on 2011-05-31
When I press "Alt+F2" I get 'panel_run_dialog'. I guess it's not the same for you then? Here is a screenshot of the box that pops up after either pressing "Alt+F2" or pressing the Windows Key after setting it using this command:

gconftool-2 --set /apps/metacity/global_keybindings/panel_run_dialog --type string "Super_R"

As such, for me, "Alt+F2" = panel_run_dialog. And "Alt+F1" = panel_main_menu. Maybe you have that reversed? IDK.

---

### Post by gyyug78fg87ogguiioioioioi on 2011-05-31
oh sorry i though it was wrong the first time u told
its right that the one i wanted thanks!;)

---

### Post by inameiname on 2011-06-01
No problem. Glad to help. 


Oh, and be sure to mark this thread as solved.

---

