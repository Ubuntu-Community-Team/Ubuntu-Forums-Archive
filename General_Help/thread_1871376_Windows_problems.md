---
title: "Windows problems"
date: 2011-10-28
forum: General Help
---

### Post by Alan.Brown on 2011-10-28
Xubuntu 11.10

When I booted up this morning I have problems with windows.  The top bar on all windows containing the minimize and close buttons has disappeared.   I cannot move or resize any window.   If I click on an item in the menu bar the drop down menu shows but disappears when I try to access it with the mouse pointer (this happens within the window too) - I can access menu items by using the Up and Down Buttons

I can't use Ctrl+Alt+Arrow or the mouse wheel to switch desktops - the number of workspaces has reverted from 4 to 1.  Can't use Alt+Tab to switch between open windows


Windows Manager in Systems Settings shows just an empty window - no access to any settings.

Somehow I have lost a number of windows/desktop settings.

Any suggestions.

TIA

Alan

---

### Post by SkiyeSounds on 2011-11-27
having the same exact issues with my xubuntu 11.04 x64. this thread says "solved" though...how did you resolve this issue?

---

### Post by SkiyeSounds on 2011-11-29
i have found a solution, and its not reinstalling the OS thankfully. 

Resolution: 
from your session, press "ctrl+alt+f1" and log in with your user name and password. 

run this command:
mv ~/.config/xfce4 ~/.config/xfce4-bk

this will back up your old folder and force (x)ubuntu to restore default look. you will be brought back to your prompt (hopefully). 

now, run this command:
DISPLAY=:0.0 xfwm4

you'll likely receive a few errors. my output was as follows:
"xfwm4:1975: GLib-CRITICAL **: g_str_has_prefix: assertion 'prefix != NULL' failed
xfwm4:1975: xfwm4-WARNING **: failed to connect to session manager: SESSION_MANAGER environment variable not defined"

after this, press "ctrl+alt+f7" to return to X (your session). you should see the tops of the windows back and it should look like it did when you first installed *buntu (default background, panels, desktop icons, etc). 
now you must add xfwm4 to the session and startup values. to do this, go to the xfce menu, and select "settings->settings manager" - once in there, click the icon for "session and startup" and go to the "application autostart" tab. add "xfwm4" as the name, add a short description and "xfwm4" as the command (sans-quotes of course). once you add it, it will be the last value on the list - make sure it is checked off (it should be by default). from there, you have to re-customize your gui, but like i said, for me thats better than reinstalling. this whole process (of re-setting up my gui also) took a total of about 15 minutes.

---

### Post by asdf42 on 2012-01-03
I had this problem a couple of times and I think my solution is even easier. You dont have to lose any configuration. 
(My xubuntu 11.10 is localized, some names I mention may not be accurate.)
  --The thing is to start xfwm4. You can run it by alt-F2. You may not be able to write in the dialog "run application" that appeares directly, so you write "xfwm4" somewhere else, mark it with your mouse and copy-and-paste it to the dialog. Button "run" works.
  --Now you will have working environment, but most of the windows will have their tops too high, hidden under the top panel and you wont be able to move them. This can be worked around easily by right-clicking on top panel -> panel -> panel properties -> autohide panel. When panel autohides, tops of windows will become accessible making the windows movable. You may set the panel-autohide back off then. 
  --And voila, everything is working fine!! (You may have to add in menu the autostart of xfwm4, as SkiyeSounds described in previous post, for this solution to be permanent even after reboot.)

---

