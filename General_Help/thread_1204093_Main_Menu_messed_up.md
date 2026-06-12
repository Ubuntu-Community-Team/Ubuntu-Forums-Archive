---
title: "Main Menu messed up"
date: 2009-07-04
forum: General Help
---

### Post by Ashin Sopaka on 2009-07-04
when clicking on the main menu icon in the panel, all the application categories have gone missing. "main menu" remains in system/preferences, but nothing happens when it is clicked on.

not sure what was done to have caused this change. any ideas on how to get it/them back?

am using jaunty, with latest updates.

thanks in advance

---

### Post by PmDematagoda on 2009-07-04
Ashin Sopaka: Please create a new thread when you want to get support on a problem instead of posting in an older, already solved thread, usually that does not confuse people into missing your question accidentally.

---

### Post by PmDematagoda on 2009-07-04
About the question, did you try running:-
```
alacarte
```
in a terminal to see if that works? If it doesn't, please post the error message here.

---

### Post by jdeppel on 2009-07-04
I think I had this same exact problem a while back. I'd click on the Applications Menu, and would be presented with a non-functional black dot instead of the menu. Places/System menus were unaffected.

To solve the problem, navigate to ~/.config/menus and delete "applications.menu" as this will force ala carte to "rebuild" the applications menu.

---

### Post by Ashin Sopaka on 2009-07-04
Hi PmDematagoda - special thanks for the advice on starting a new thread - relative nOOb, so still working on the etiquette!

Also, thank you again and jdeppel for the alacarte suggestion! It worked!!!

For the sake of edification, in that folder were quite a few application.menu files, each one appended with .undo10, .undo11, etc. Same with settings.menu. How are these files created and what do they mean?

Thanks again

---

### Post by hatakah on 2009-09-05
Thank you so VERY much! You have no idea how long this has been messed up...
Now...I've got missing apps to track down.

---

