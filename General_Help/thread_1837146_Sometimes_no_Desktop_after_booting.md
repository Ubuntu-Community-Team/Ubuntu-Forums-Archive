---
title: "Sometimes no Desktop after booting"
date: 2011-09-01
forum: General Help
---

### Post by Noble Bell on 2011-09-01
I am running Ubuntu 11.04 32-bit on a Toshiba  Satellite P305D laptop with an ATI graphics adaptor. I do not have any proprietary drivers installed. It is pretty much a straight out of the box install and update system. I am new to trying Linux.

Problems that I am having are:

1) Sometimes when my machine boots I get a login display and I type in my password. The desktop background comes up and the startup music plays. Then nothing else happens no GUI.  (I can shut down and restart several times and it will eventually come up)

2) Sometimes on the display (when it is working) I will get weird graphics clutter on some of the icons and such in the launcher menus.


Can anyone offer any suggestions on how to correct these problems? As stated, I am new to Linux and I really want to give it a fair try before making up my mind on switching completely over. I have been in computers as a developer for 25+ years on Windows/Mac.

---

### Post by xtremesupremacy3 on 2011-09-04
I can't promise how much use I can be to solving your problem but let's see if it's a graphics driver issue.

Start up the computer and straight after BIOS has loaded, hit the left Shift button, which should take you the grub menu.

Next hit 'e' (without quotes)

find the line that says 'quiet splash' and replace that with 'nomodeset' 

Finally hit Ctrl+X to startup, does that give you any problems.

If no, you should be alerted that there are proprietary drivers for your card, I recommend installing that

---

