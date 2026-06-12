---
title: "Shortcut in Applications Menu Doesn't Run Correctly"
date: 2010-04-28
forum: General Help
---

### Post by RJG on 2010-04-28
I've added Warsow.i386 (0.5) to my Applications > Games menu as a shortcut, but whenever I try to run it, my screen goes black for a second and then returns to desktop. Running the same file from its folder in /home runs the game fine.

Is this a common problem with shortcuts or is it just me and the game?

---

### Post by colorlessprism on 2010-04-28
are you able to start the program from the ALT+F2 menu? i would open System-->Preferences-->Main Menu and "edit" the shortcut to see the command
i had thunderbird installed once where i could not start it by "thunderbird" i had to use "~/.thunderbird/thunderbird" to get it started

---

### Post by dcstar on 2010-04-28
> **RJG said:**
> I've added Warsow.i386 (0.5) to my Applications > Games menu as a shortcut, but whenever I try to run it, my screen goes black for a second and then returns to desktop. Running the same file from its folder in /home runs the game fine.

Is this a common problem with shortcuts or is it just me and the game?

Linux does not have "Shortcuts", what are you talking about?

---

### Post by RJG on 2010-04-28
> **dcstar said:**
> Linux does not have "Shortcuts", what are you talking about?

Right click on the menu, select "EDIT MENU". Select the target menu (in this case games) on the left and then hit the "New Item" button. Provide a link to the app you want added to the menu (in this case the warsow.i386 that launches the game from inside it's folder in /home) and hit done.

I did it this way because I downloaded the unified 0.5 zip for Warsow via the website rather than through the Ubuntu Software Centre, but for some reason it doesn't like

[QUOTE=colorlessprism]are you able to start the program from the ALT+F2 menu? i would open System-->Preferences-->Main Menu and "edit" the shortcut to see the command
i had thunderbird installed once where i could not start it by "thunderbird" i had to use "~/.thunderbird/thunderbird" to get it started[/QUOTE]

No luck with that. I have launched it from inside a terminal using ./warsow.i386 and it runs, albeit not as well as if I simply double click the icon in the folder.

EDIT: Also, supplying the full path (/home/rjg/Games/warsow_0.5_unified/warsow.i386) for the ALT+F2 Run dialog box simply does the same thing as the shortcut in the Applications menu.

EDIT 2: If I simply remove the .i386 file extension from the Run command it works fine. I'm not sure why that is (Unix newbie here) but it, like everything else recently, has been a learning experience. Thanks for your help guys.

---

