---
title: "Jaunty Inverted Menu bar, PLEASE HELP!"
date: 2009-07-05
forum: General Help
---

### Post by sur2124 on 2009-07-05
Hello guys,
 I am new to ubuntu, and have come across a problem that I am unable to find any solutions to. You know on every window, on the left hand side of the menu bar, there are the maximize, minimize and exit buttons for that window. Well, the other day I was messing around with the appearance settings, and somehow those three buttons are now on the right hand side of every menu. This is very annoying. I have been tinkering with the appearnance settings trying to get it to go back to no avail. 

Please help me.

Thanks!

---

### Post by ajgreeny on 2009-07-05
It is more likely a cuatom change you have made in the details of the theme you are using.

Go back to appearance, and in the theme tab, see if you can put things right again.

---

### Post by CatKiller on 2009-07-05
Are you using Emerald or Metacity as your window decorator?

If it's Metacity, open up gconf-editor and change the /apps/metacity/general/button_layout key to your satisfaction.

If it's Emerald, use System -> Preferences -> Emerald Theme Manager and go to Edit Themes to change the Title-bar Object Layout setting to your satisfaction.

---

