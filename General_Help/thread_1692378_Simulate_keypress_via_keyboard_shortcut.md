---
title: "Simulate keypress via keyboard shortcut"
date: 2011-02-21
forum: General Help
---

### Post by AlphaWeapon on 2011-02-21
Hi, sorry for being so egoistical but I kind of need help.
I have a G15v1. After going through hoops and loops to get it working only to discover that you only needed to install g15daemon through the Ubuntu Software Center, I found myself with one big problem.
I migrated from windows just now, and there, I had my macro keys(the extra ones) bound to CTRL+W, CTRL+T and to a simulated mouse-wheel scroll so I could navigate the web more easily.
How would I go about doing that?
I figured, if I used the System->Preferences->Keyboard Shortcuts thingy and bound my key, in my case XF86Launch5, to a command similar to "simulate keypress CTRL+W"(I know it's totally wrong, just to give you an idea), I might be able to get it working again. Only problem is, I can't find anything like that. Any of you has any clue about it? I googled but I only find C++/Java/coding related results, which are not exactly what I need to do.
Please help? I know it seems like nothing but it's really preventing me to stick with Linux as that would blow all my "YOU CAN DO ANYTHING" bubble...

---

### Post by coldraven on 2011-02-21
Did you actually try System->Preferences->Keyboard Shortcuts?
I just did and mapped the unused Compaq "Help" button to "home folder" and believe or not it works.

---

### Post by AlphaWeapon on 2011-02-21
> **coldraven said:**
> Did you actually try System->Preferences->Keyboard Shortcuts?
I just did and mapped the unused Compaq "Help" button to "home folder" and believe or not it works.
Yeah, I managed to map them to anything I want application-wise, but I need that button to work as if I pressed CTRL+W

---

### Post by AlphaWeapon on 2011-02-22
up please? I kept trying and I found nothing.
KDE has something like this, but I prefer gnome vastly.

---

### Post by AlphaWeapon on 2011-02-23
up...

---

### Post by bratherlui on 2012-03-06
For assigning an alternative XF86AudioPlay when using an USB-keyboard I did the following to let banshee (mediaplayer) pause/play
Put the afterwards following lines into a script/file in your home( may be /home/$username/mp_play.sh )
Run the command in the terminal in the folder
$ chmod +x ~/mp_play.sh
Go into Keyboard-preferences (don't know the english title, just a guess) where the shortcuts can be defined, add a new one, that calls the script with the command /home/$username/mp_play.sh
The commented out #gnome-terminal was just for seeing immediate results if the short-cut pressed. To see immediate results  remove the #

#!/bin/bash
#gnome-terminal
WID=`xdotool search banshee | head -n1`
xdotool windowactivate $WID
xdotool key XF86AudioPlay

---

### Post by HiImTye on 2012-03-06
to send Ctrl+W using [xmacroplay]("apt://xmacro")[FONT=monospace][/FONT] go to keyboard then the shortcuts tab, select 'custom shortcuts' and click the '+' at the bottom. name it whatever you want, then in 'command' put the following:
```
echo KeyStrPress Control_L KeyStr w KeyStrRelease Control_L | xmacroplay $DISPLAY
```
on the right side, where it says 'disabled' click, then press the key you want to use.

modify this for whatever key you want

---

