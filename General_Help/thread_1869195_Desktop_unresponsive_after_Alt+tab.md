---
title: "Desktop unresponsive after Alt+tab"
date: 2011-10-25
forum: General Help
---

### Post by diversecg on 2011-10-25
I am having a strange problem after using Alt+tab to switch between applications.  Somehow the desktop becomes completely unresponsive to any input except moving the mouse.  ctrl+alt+del or clicking does nothing, but the machine is not frozen, I am still able to do Ctrl+Alt+F1 and get a term.  There is no processes hanging, and even tried killing all unity processes and still unresponsive after going back with Ctrl+Alt+F7.  The only option is to do a sudo reboot in the terminal, loosing all open work and applications of course.  I installed 11.10 on a few machines and for the most part no major problems.  I have had this happen a 3 times in the past week, but I am unable to pinpoint the exact cause.

The only commonality when it happens is trying to switch applications using Alt+tab and selecting the desktop.  I have also had it happen clicking on the menu by accident when it pops open when I was trying to click on a window behind the current window, it menu opened partially and everything hung in the same fashion.   To make things worse I am unable to reproduce the issue.

Posting this in the hopes others may have seen this particular issue, it looks like the computer is completely frozen, and unless the user knows to use Ctrl+Alt+F1 to get term, they would have to force the machine down as pressing the power button does not respond/bring up shutdown menu (even if power button is set to shutdown without asking)

edit:
Well, it is not specifically Unity causing the issue, it appears to be compiz (go figure, always causes problems)  It appears that compiz or something related to it takes complete focus  preventing any desktop interaction (usually happens switching screens  with a alert/dialog that poped up somewhere in the background from any  application)

solution: use Ctrl+Alt+F1 to get to terminal, login, then kill compiz:

sudo killall -KILL compiz

After that Ctrl+Alt+F7 brings back desktop (reorganizing itself as compiz/unity starts again automatically) and everything appears to work again

---

