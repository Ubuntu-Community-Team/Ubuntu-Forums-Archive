---
title: "cant access shut down menu please help"
date: 2010-06-24
forum: General Help
---

### Post by cschamber on 2010-06-24
i can't access my shutdown menu due to over lapping mirror images of my name and date on the top right side of my gnome gui screen. I am running ubuntu 10.04 please help or ill be forced to have to leave my computer on FOREVER !!!! ( lol kidding on the leaving on forever part i know how to shut down with terminal, but the mirror image covering my graphical shutdown menu is quite annoying )

---

### Post by ThesaurusRex on 2010-06-24
What's with these mirror images of name/date? Did you do that on purpose? Is your question how to shutdown without the terminal and without access to that button or how to get rid of the mirror image?

Solutions for shutting down:
1. Create a launcher, and have it open in terminal with the shutdown now command.
2. Right click Panel->Add to Panel->Shut down icon (I use Xubuntu, mine is "Log Out")

Please clarify your question for more help.

---

### Post by coolman98 on 2010-06-24
Fire up a terminal and
```
 reboot
```

---

### Post by cschamber on 2010-06-24
i need to get rid of the mirror images so i can access my shutdown menu, so i guess my issue is getting rid of the mirror images of my date/time and name, attached is a screen shot look at the top right and you'll see what i mean.

---

### Post by ThesaurusRex on 2010-06-24
Your problem is potentially that you have added an extra item to your panel (the extra item being username and/or date). Try to right-click->Remove Item on those "mirror images."

Does this happen every time you reboot?

---

### Post by Devil999 on 2010-06-24
I've also had this problem. It only happens sometimes, but it's quite anoying. I must use the shutdown key to acess the shutdown menu, because the overlap turns those menus unusable.

---

### Post by cschamber on 2010-06-24
thanks for the info, problem resolved.

---

### Post by bim on 2010-09-28
How did you resolve it? Calling the terminal? I have the same problem without have added new menus or icons, That seems a bug in the gnome interface, isn't it?

---

### Post by cschamber on 2010-09-28
I ended up just right clicking and selecting remove from panel, then I re added it

---

