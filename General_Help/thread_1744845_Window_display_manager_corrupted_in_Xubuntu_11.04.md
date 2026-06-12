---
title: "Window display manager corrupted in Xubuntu 11.04?"
date: 2011-04-30
forum: General Help
---

### Post by Pgimps on 2011-04-30
So I upgraded to 11.04 last night, installed all the updates and reconfigured all my apps, Virtualbox, exile, etc. This morning I wake up and my top bar on all my applications were gone no exit, minimize, maximize were gone so being the jenius I was I went to google and typed in my problem, and I found a solution with the command 

patrick@patrick-P50IJ:~$ metacity --replace 

and it replaced it with an ugly interface how would I go about restoring it

P.S. when ever I try to go into the manager the window is just blank except for the back button?patrick@patrick-P50IJ:~$ metacity --replace^C

---

### Post by keithpeter on 2011-05-01
> **Pgimps said:**
> So I upgraded to 11.04 last night, installed all the updates and reconfigured all my apps, Virtualbox, exile, etc. This morning I wake up and my top bar on all my applications were gone no exit, minimize, maximize were gone so being the jenius I was I went to google and typed in my problem, and I found a solution with the command 

patrick@patrick-P50IJ:~$ metacity --replace 

and it replaced it with an ugly interface how would I go about restoring it

P.S. when ever I try to go into the manager the window is just blank except for the back button?patrick@patrick-P50IJ:~$ metacity --replace^C

Just a guess, and maybe a long shot, but try restarting Xubuntu (log out/log in or just restart) then load a window and then press and hold the ALT key and press F11. 

Alt-F11 'toggles' a feature in Xubuntu where you can hide the window decorations.

[http://www.keyxl.com/aaac887/409/Xfce-Window-Manager-keyboard-shortcuts.htm](http://www.keyxl.com/aaac887/409/Xfce-Window-Manager-keyboard-shortcuts.htm)

---

