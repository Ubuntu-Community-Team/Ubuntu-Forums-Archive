---
title: "compiz configuration gone wrong"
date: 2010-08-02
forum: General Help
---

### Post by rockager on 2010-08-02
help! i have accidentally configured compizconfigure settings manager to activate the shift switcher whenever i press the left mouse button.
because of this now i cant do any work
as the shift switcher is activated whenever i press the left mouse button

i tried to use remove compiz by typing this command in the terminal:
sudo apt-get remove compiz
the terminal said that it has been removed but but it is still in the system>>preferences menu and the shift switcher still gets activated when i press the left mouse button.:(
what should i do?
please help!!

---

### Post by ajgreeny on 2010-08-02
Alt+F2 to get the run dialog, then type ```
metacity --replace
``` and hit enter.  That will stop compiz running, whereas simply uninstalling it will not until you reboot or restart x, or just stop compiz with that command.

---

### Post by hariks0 on 2010-08-02
No need to go to extremes like 'remove'. Just use your keyboard to start 

Alt+F1 > Preferences > ccsm > Mouse wheel to reach the shift switcher in Window management> Space to deselect.

:popcorn:

---

### Post by ajgreeny on 2010-08-02
> **hariks0 said:**
> No need to go to extremes like 'remove'. Just use your keyboard to start 

Alt+F1 > Preferences > ccsm > Mouse wheel to reach the shift switcher in Window management> Space to deselect.

:popcorn:
What is Alt+F1 supposed to do?  It does nothing on my machine.  Did you mean Alt+F2?

I suspect you confused the OP, as I did not understand what you meant, and your suggested pathway gets me nowhere.

---

### Post by hariks0 on 2010-08-02
The original configuration of Ubuntu will launch the main menu if Alt+F1 is pressed. Then follow the path :-

System>Preferences>Compiz config Settings Manager> Right click at the down arrow in the CCSM window to reach the window management module>Right click on Shift switcher check box [Nothing will happen except that the control will be at the check box to select it] > Press space to deactivate.

Hope it is rather clear :p

PS: You can type ccsm in Alt+F2 or in terminal to launch compiz config settings manager.

---

### Post by ajgreeny on 2010-08-02
> **hariks0 said:**
> The original configuration of Ubuntu will launch the main menu if Alt+F1 is pressed. Then follow the path :-

System>Preferences>Compiz config Settings Manager> Right click at the down arrow in the CCSM window to reach the window management module>Right click on Shift switcher check box [Nothing will happen except that the control will be at the check box to select it] > Press space to deactivate.

Hope it is rather clear :p

PS: You can type ccsm in Alt+F2 or in terminal to launch compiz config settings manager.
I don't think the Alt+F1 has ever done that on my machine, and I have not changed any settings that I can remember, hence my question.  To get the menu to show I press my right "windows" key; it was the left one but I changed that as I have many compiz plugins with a left "windows" + a letter key.

However, with the mouse left click not working, I still don't see how getting the menu to show will help, as a left click will just start the Shift switcher, won't it?   Or will that not be the case once the menu is showing?

I still think it easier to use the **metacity --replace** command and then change the CCSM settings when compiz is not running.

---

### Post by Quackers on 2010-08-02
Alt + F1 shows my Applications menu

---

### Post by hariks0 on 2010-08-03
> **Quackers said:**
> Alt + F1 shows my Applications menu

Should I add

*Press -> [Right arrow] twice to Reach System menu.*

---

### Post by ajgreeny on 2010-08-03
> **Quackers said:**
> Alt + F1 shows my Applications menu
OK, I obviously must have changed away from the default at some time in the past.

However, I use the **main menu** not the **menu bar** so I wonder if that makes a difference;  anyone know?

---

### Post by hariks0 on 2010-08-03
In main menu, instead of menu bar. the System menu will be at the bottom - above logout [if it is there].

---

### Post by ajgreeny on 2010-08-04
Yes, I know that and everything is in my menu, no problem.

I was just wondering if the lack of an Alt+F1 bringing up the menu was the result of me using the main menu instead of menu-bar.

---

### Post by hariks0 on 2010-08-04
No. It is not like that. Please refer the first link in my signature for the details.

Drop in a line in that post if you found that useful.

:popcorn:

---

### Post by rockager on 2010-08-04
thanks for helping me out! you guys are great! :)

---

