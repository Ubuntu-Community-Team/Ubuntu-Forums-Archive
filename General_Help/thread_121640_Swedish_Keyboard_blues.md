---
title: "Swedish Keyboard blues"
date: 2006-01-25
forum: General Help
---

### Post by ububaba on 2006-01-25
Have tried to configure Ubuntu so that I can type in Swedish as well. Tried System/Preferences/Keyboard/Keyboard Preferences/Layouts... No luck at all.  Any experts around?

---

### Post by slashem on 2006-01-25
You can try this:
1. sudo dpkg-reconfigure xserver-xorg  

or this:
 
1. Edit this section in  /etc/X11/xorg.conf :

> 
Section "InputDevice"[INDENT]Identifier      "Generic Keyboard"
Driver          "kbd"
Option          "CoreKeyboard"
Option          "XkbRules"      "xorg"
Option          "XkbModel"      "pc105"
Option          "XkbLayout"     "se"[/INDENT]EndSection


(and for both cases...) :

2.  Push Ctrl+Alt+Backspace (this restarts the xserver)

3. Log in

4. Hopefully it works...

---

### Post by ububaba on 2006-01-25
I tried. Sorry but being a newbie, probably I messed up everything. These steps were above my head. May be you haven t come accross any one like me before. I tried to locate site which cover the subject. No luck yet.

---

### Post by slashem on 2006-01-25
Well, try this:

Right-click on the top panel.

Choose "Add to panel..."

In that window, choose "Keyboard Indicator" and push the "Add" button

Right-click the Keyboard Indicator

Choose "Open Keyboard Preferences"

Choose the "Layouts" tab

Push the "Add" button

Choose "Sweden" and "OK"

Tick off "Sweden" and "Close"


Hope this helps, but Keyboard Indicator seems buggy to me, so it might not.

:)

---

### Post by ububaba on 2006-01-25
After this point downwards did not work.  When I push the "Add" button it hopped and the "Add to panel" screen disappeared. It is buggy alright. Had to restart the process but it was the same story again. Unfortunately.


> 
In that window, choose "Keyboard Indicator" and push the "Add" button

Right-click the Keyboard Indicator

Choose "Open Keyboard Preferences"

Choose the "Layouts" tab

Push the "Add" button

Choose "Sweden" and "OK"

Tick off "Sweden" and "Close"


:)

---

### Post by dcstar on 2006-01-25
[QUOTE=ububaba]After this point downwards did not work.  When I push the "Add" button it hopped and the "Add to panel" screen disappeared. It is buggy alright. Had to restart the process but it was the same story again. Unfortunately.[/QUOTE]
Just drag the icon to the place on the panel where you want it to be.

---

### Post by ububaba on 2006-01-25
[QUOTE=dcstar]Just drag the icon to the place on the panel where you want it to be.[/QUOTE]
David I followed your instructions. In the panel I see "Swe", indicator of the keyboard for Swedish. One can eventually see the keyboard layout view as well by clicking. Well and good, however the keyboard itself still follows the UK layout, when I try to type. It has not been converted.

---

### Post by dcstar on 2006-01-25
[QUOTE=ububaba]David I followed your instructions. In the panel I see "Swe", indicator of the keyboard for Swedish. One can eventually see the keyboard layout view as well by clicking. Well and good, however the keyboard itself still follows the UK layout, when I try to type. It has not been converted.[/QUOTE]
Do you have an "Intl" keyboard selected in Preferences?

---

### Post by ububaba on 2006-01-26
[QUOTE=dcstar]Do you have an "Intl" keyboard selected in Preferences?[/QUOTE]
In reality I have a Compac with 101 keys while the Device Manager says it is "IBM Enhanced (101/102) keys". I have tried every possible choice in Preferences. Even "Generic Intl". I will follow your command.

---

### Post by ububaba on 2006-01-26
I was away from the computer for some time. It apparently had crashed, as the Login page was being shown. After login, I discovered that Swedish keyboard was active. God and Ubuntu move in mysterious ways.

---

