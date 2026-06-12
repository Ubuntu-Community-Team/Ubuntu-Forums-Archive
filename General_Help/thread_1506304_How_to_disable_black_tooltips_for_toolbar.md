---
title: "How to disable black tooltips for toolbar?"
date: 2010-06-10
forum: General Help
---

### Post by pstein on 2010-06-10
When I hoover over toolbar menu entries like "System" then currently tooltips (with black background) appear like
 
"Change system appearance and behaviour, or get help"
 
How can I disable these tooltips (for the standard Ubuntu menues only, if possible) ?
 
Peter

---

### Post by monymirza on 2010-06-10
1) Go to the main menu bar and right-click **Applications**  --> **Edit Menus**... note that this is a right-click,  not a "normal" click. 

2) In the left side of the window (labeled **Menus:**),  click on **System Tools**. 

3) In the right side of the window, click on **Configuration  Editor** to enable it. Once enabled, there will be a checkbox  next to it. If there is already a checkbox next to it when you get here,  then you do *not* need to click on it. 

4) Click **Close** to close this window. 

5) Go back to the main menu bar and click  **Applications**  --> **System Tools** --> **Configuration  Editor**. 

6) In the left side of the configuration editor, navigate to **apps**  > **panel** > **global**. 

7) Once **global** is selected go to the right side and  click on **tooltips_enabled** to *remove* the  checkbox next to this.  

8) With the checkbox now gone, go to **File** --> **Close**  to close the configuration editor. 

Once this is done, you should no longer have tooltips on your Ubuntu  Gnome desktop.

---

### Post by pstein on 2010-06-10
Ok, thank you.
And what about the tootips for
- Timestamp
- Keyboard indicator
 
in Toolbar?
There are still shown
 
Peter

---

### Post by doublewitt on 2010-08-14
I found the solution (for me),

"The way to get rid of ALL tool tips is open your Compiz Config Settings Manager, enable "Opacity, Brightness and Saturation" under "Accessibility". Click on the button to go into the settings.

Under the "Opacity" tab go down to "Window Specific Settings" and click "Add". Type "Tooltip" and slide the opacity down to zero. Click "Close".

You're done."

[NB: It is possible you already have "Tooltip" included under another entry, for example if you've made your menus, popups, dropdowns etc transparent. If so just edit that entry and remove "Tooltip" form it so you don't have two conflicting opacity settings.]

from:  [http://geekybits.blogspot.com/2007/07/ubuntu-tip-turning-off-tooltips.html]("http://geekybits.blogspot.com/2007/07/ubuntu-tip-turning-off-tooltips.html")

**[SIZE="6"]*[/SIZE]**there are other alternatives on this page...

---

