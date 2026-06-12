---
title: "ibus causes application crash when typing chinese (other alternatives to ibus?)"
date: 2010-07-31
forum: General Help
---

### Post by janoochen on 2010-07-31
I'm using:
- Ubuntu 10.04 LTS Lucid Lynx
- ibus 1.2.0.20091215-1ubuntu4
- ibus-m17n 1.2.0.20091217-1
- ibus-table 1.2.0.20100111-1


 Every time I type Chinese characters in Firefox, Gedit, Chromium (I  believe any application) using ibus bopomofo (m17n) that application  freezes (only the current application), but I still can move the mouse  and click the close windows (but it doesn't work), then I just click  "Force Quit" which pops up seconds later.


 I noticed that it happens when I type and change the input method (Ctrl + Space) two or three times (within any period of time).


 I also did following to make ibus start automatically:
 1]
 Under System->Administration->Language Support
 For "Keyboard input system" choose "ibus"
 2]
 Under System->Preferneces->Startup Applications
Click on "Add" and fill min dialog box as
 Name: iBus
Command: ibus-daemon -drx
Comment: the ibus demon
 Now click "Add"
 3]
Open .bashrc in an editor (e.g. gedit) and add the following lines:
 export GTK_IM_MODULE=ibus
export XMODIFIERS="@im=ibus"
export QT_IM_MODULE=ibus
 
(There are other reported bugs with Chinese>py input method where ibus crashes the application)

Is ibus really in beta stage? 
Is there a way of fixing this problem with Chinese inputs? 
Is there more stable alternatives?

---

