---
title: "starting terminal in top right corner"
date: 2010-05-31
forum: General Help
---

### Post by elidoperezmd on 2010-05-31
Hi all... 
When i start the terminal it opens in the top left corner of the screen, is there any way of setting it to start in the top right corner of the screen instead. And also to adjust the size wich it opens with?

Thanks for the replies/time

---

### Post by WorMzy on 2010-05-31
You can modify the size by editing the default terminal profile (right-click inside a terminal, hover over Profiles, and choose Profile Preferences).

Regarding the window placement, I think that the Place Windows plugin in Compiz will do what you want.

---

### Post by elidoperezmd on 2010-05-31
ok the size is fixed, thanks to ur help.

But i done know how to get 1 single window (terminal in this case) to be placed in top right corner....seems that when i set the changes in compiz/windows place, every window goes out of the screen and only their edges show

---

### Post by elidoperezmd on 2010-05-31
thing are worst here...whenever i poen a window it will show aoutside the desktop (all desktops)

---

### Post by WorMzy on 2010-05-31
Can you move them back onto the screen with Alt+F7 and the arrow keys? (or right-click on the window's Window List item and choosing Move)

After playing with the settings myself, I can get my terminal to always open in the top right by adding a custom rule to the Fixed Window Placement tab of the Place Windows plugin.

The rule is (under "Windows with fixed placement"):
```

Positioned windows: class=Gnome-terminal
X Positions:        10000
Y Positions:        0
Keep in workarea:   true
```

The 10000 can be replaced with any arbitrary value you want, so long as it's greater than your screen resolution's pixel width.

---

### Post by elidoperezmd on 2010-05-31
solved...thanks

---

### Post by elidoperezmd on 2010-09-15
sorry for coming out of the blue with this...how can i make it appear "always on top" of all the other windows?

thanks for your time

---

### Post by WorMzy on 2010-09-16
There's an option for that in the Windows Rules plugin, under Matches.

---

### Post by elidoperezmd on 2010-09-16
above maybe? anf then grab? grab the terminal and thats it? if so...not working for me

:(

---

### Post by elidoperezmd on 2010-09-16
forgot to fil in the field..dumb

solved..thanks again

---

### Post by WorMzy on 2010-09-16
The latest version of ccsm doesn't seem to work correctly when grabbing windows. It grabs the information but doesn't append it to the text boxes when you click OK. Kinda annoying.

But glad I could help.

---

