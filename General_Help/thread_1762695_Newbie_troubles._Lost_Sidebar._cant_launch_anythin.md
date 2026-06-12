---
title: "Newbie troubles. Lost Sidebar. cant launch anything."
date: 2011-05-19
forum: General Help
---

### Post by Meiketsu on 2011-05-19
Ok So i was trying to figure out how to use the compiz thing so i can have all the fun eyecandy stuff running so i downloaded the Advance compiz utilitie and i went to turn on cube desktop and when i did my side toolbar went away and all the controlls to close windows are gone.. Help me get all my controlls back to normal! I had to find a way to get Firefox to open for me through Plants Vs. Zombies because i cant find my firefox icon D:  Someone please help

---

### Post by Meiketsu on 2011-05-19
I seriously need some help. All ive managed to find i can do is hold Ctrl + alt and drag my desktop around to see a secondary desktop, I cant get the Compiz manager to open or any application. I have no Minimize,fullscreen or X button on my windows, i have no sidebar with all my applications so i cant open anything. I dont even have a function to shut down my pc aside from the manual power button D: someone save me D:

---

### Post by lmn. on 2011-05-19
for window controls you can try..

opening the terminal and typing gconf-editor
apps>metacity>general
change button layout to [FONT=Courier New][SIZE=2]menu:close[/SIZE][/FONT]

---

### Post by StrayEddy on 2011-05-19
Ctrl+Alt+T to open a terminal

---

### Post by lmn. on 2011-05-19
also uninstall/reinstall compiz & restart

sudo aptitude remove compiz..

---

### Post by StrayEddy on 2011-05-19
To uninstall:
sudo apt-get remove compiz
If there is more then one option of compiz use:
sudo apt-get remove compiz* (be carefull to know what you are uninstalling before doing so)
 
To install:
sudo apt-get install compiz

---

