---
title: "Ubuntu not responding after login keyring"
date: 2011-03-09
forum: General Help
---

### Post by tadness on 2011-03-09
Hi all. 
I joined just so I could post this. I'm having big problems in Maverick. 
I was attempting to install a program in WINE when my laptop crashed from overheating (bad motherboard I can't really afford to replace). It logged in as usual, but a login keyring dialog box popped up.
I can't type anything in to get rid of it, nor will anything else work. Clicking buttons does nothing. No button combinations work except for CTRL+ALT+F2. Afterwards I am able to type commands, but I don't know enough about the Terminal to really get around.

The really odd thing is that on the desktop, the cursor moves about, but the only thing that responds to it is when I hover over icons in Docky, which causes them to magnify, but I am unable to click on them. Nothing else even shows a tooltip or changes at all, so I suppose Docky may be the problem.

I'd like to note I've had problems with Ubuntu not recognizing my trackpad before, in which case I used the keyboard, but this is with a USB mouse, which it recognizes, just not any of the click commands.

Please, someone help! Really desperate here!


***EDIT: Problem solved.** Went into recovery mode in low-graphics mode, and  was able to enter my login keyring password and uninstall the program  that was causing trouble. (Gnome-Do)*

---

### Post by Paulgirardin on 2011-04-01
I'm having exactly the same problem.I installed Gnome Do.

I get the same dead keyboard and mouse keys ,cursor moves and Cairo dock responds on mouse over.
I rebooted into recovery mode and changed auto login to manual.

I will try uninstalling gnome do

---

### Post by rayburn on 2011-04-06
Thank you! This solution, of uninstalling gnome-do worked for me as well.

---

