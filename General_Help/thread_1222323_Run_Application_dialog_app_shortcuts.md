---
title: "Run Application dialog app shortcuts?"
date: 2009-07-24
forum: General Help
---

### Post by thefsfempire on 2009-07-24
Rather than typing in 'gnome-terminal' is it possible to make a symbolic link such as 'gterm' and save myself from typing a little? Not trying to be lazy just simply curious.

---

### Post by starcraft.man on 2009-07-24
If you find yourself using a terminal very often, I'd just save yourself time and install a drop down terminal that launches at start up and remains. On KDE look for yakuake in GNOME look for a package called tilda. Both are good, basically you assign them a key say tilda or F1 and then you can call them down as needed.

Alternatively, if you want to go look up basic bash scripting. There are numerous ways I'm sure, I'm just a beginner. One option is set a variable for say gtrm to expand to gnome-terminal. Then put it in one of the start up scripts. I don't have any tuts off hand for this, though a quick search of forums or google will find you many better explained. IMO, the first option is better.

---

### Post by thefsfempire on 2009-07-25
Hey thanks! I never really thought of assigning a keyboard shortcut. I followed your advice on Tilda and looked into that one where I found it you can use it like an in-game console. I decided to look into the keyboard shortcuts (gconf-editor: apps/metacity/keybindings and global keybindings + enabling commands in ccsm) and everything works great. I have gnome-terminal up and running the way I like so I didn't want to move terms just yet.

Thanks!

---

### Post by CatKiller on 2009-07-25
The Run dialogue has auto-completion, and does remember what you've typed. If, for example, gconf-editor was the last thing you ran in the Run dialogue, Alt-F2&#8594;down arrow&#8594;Enter would run it again. Most people don't like typing much when they don't have to.

---

