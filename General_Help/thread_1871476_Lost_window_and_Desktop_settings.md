---
title: "Lost window and Desktop settings"
date: 2011-10-29
forum: General Help
---

### Post by Alan.Brown on 2011-10-29
Xubuntu 11.10  -  has been working well until now.

When I booted up this morning I have problems with windows.  The top bar  on all windows (above the Menu Bar) containing the minimize and close buttons has  disappeared.   I cannot move or resize any window.   If I click on an  item in the menu bar the drop down menu shows but disappears when I try  to access it with the mouse pointer (this happens within the window too)  - I can access menu items by using the Up and Down Buttons

I can't use Ctrl+Alt+Arrow or the mouse wheel to switch desktops - the  number of workspaces has reverted from 4 to 1.  Can't use Alt+Tab to  switch between open windows   Can't make any changes to the Panel settings

Windows Manager in Systems Settings shows just an empty window - no access to any settings.

Somehow I have lost a number of windows/desktop settings.

Any suggestions.

TIA

Alan

---

### Post by oldtimer7777 on 2011-10-29
Did this happen after you installed the latest updates? Just curious..

> **Alan.Brown said:**
> Xubuntu 11.10  -  has been working well until now.

When I booted up this morning I have problems with windows.  The top bar  on all windows (above the Menu Bar) containing the minimize and close buttons has  disappeared.   I cannot move or resize any window.   If I click on an  item in the menu bar the drop down menu shows but disappears when I try  to access it with the mouse pointer (this happens within the window too)  - I can access menu items by using the Up and Down Buttons

I can't use Ctrl+Alt+Arrow or the mouse wheel to switch desktops - the  number of workspaces has reverted from 4 to 1.  Can't use Alt+Tab to  switch between open windows   Can't make any changes to the Panel settings

Windows Manager in Systems Settings shows just an empty window - no access to any settings.

Somehow I have lost a number of windows/desktop settings.

Any suggestions.

TIA

Alan

---

### Post by Alan.Brown on 2011-10-29
I am not sure - I think that was when it happened.   I updated yesterday evening then had the problem first thing this morning.

I want to avoid re-installing if possible.  I think there is a way of resetting the settings.   

Alan

---

### Post by oldtimer7777 on 2011-10-29
> **Alan.Brown said:**
> I am not sure - I think that was when it happened.   I updated yesterday evening then had the problem first thing this morning.

I want to avoid re-installing if possible.  I think there is a way of resetting the settings.   

Alan

I have read a few other users who have been having the same problem with Xubuntu after the last round of updates..  If it is the updates, you would need to rollback to 11.04 or something that works.  The latest versions of Ubuntu are usually (but not always) buggy. I was playing around with 11.10 lately, but it isn't really ready for solid production yet. It got kinda frustrating.

---

### Post by Alan.Brown on 2011-10-29
I have Ubuntu and Kubuntu on the same computer so I may just wait until Xubuntu updates fix the problem

I like the Xfce interface

Alan

---

### Post by oldtimer7777 on 2011-10-29
> **Alan.Brown said:**
> I have Ubuntu and Kubuntu on the same computer so I may just wait until Xubuntu updates fix the problem

I like the Xfce interface

Alan

I tried Xfce.. Wasn't too happy with it. Almost took up the same amount of resources as straight Ubuntu.  Now Lubuntu/LXDE has a smaller resource footprint.  I recommend that. I'm running LXDE with Openbox..  92Mb processes at Idle.

---

### Post by Toz on 2011-10-29
> **Alan.Brown said:**
> Xubuntu 11.10  -  has been working well until now.

When I booted up this morning I have problems with windows.  The top bar  on all windows (above the Menu Bar) containing the minimize and close buttons has  disappeared.   I cannot move or resize any window.   If I click on an  item in the menu bar the drop down menu shows but disappears when I try  to access it with the mouse pointer (this happens within the window too)  - I can access menu items by using the Up and Down Buttons

I can't use Ctrl+Alt+Arrow or the mouse wheel to switch desktops - the  number of workspaces has reverted from 4 to 1.  Can't use Alt+Tab to  switch between open windows   Can't make any changes to the Panel settings

Windows Manager in Systems Settings shows just an empty window - no access to any settings.

Somehow I have lost a number of windows/desktop settings.

Any suggestions.

TIA

Alan

Sounds like the window manager has crashed and has not restarted. Press Alt+F2, enter ```
xfwm4 --replace
```...and press the run button. Should get you back where you want to be.

---

### Post by Alan.Brown on 2011-10-29
"**xwfm4 --replace**" did not seem to work

So I entered "**xwfm4**" by itself and it worked.   I set the system to save settings on shutdown and then rebooted.

All is now back to normal.

Thanks for your help

Alan

---

### Post by Toz on 2011-10-29
For clarification sake, the xfce window manager is **xfwm4** - note the spelling. 

Nevertheless, glad it worked out for you.

---

### Post by Alan.Brown on 2011-10-30
Sorry bout that.    It was spelled correctly when I entered it obviously but was miss-spelled  in the post.   Thanks for the correction.

Alan

---

