---
title: "4 desktops?"
date: 2010-07-20
forum: General Help
---

### Post by DrWeedBot on 2010-07-20
i'm kinda new to Ubuntu Netbook remix so does any one know how to add multiple desktops on the taskbar ?

---

### Post by Brandel Valico on 2010-07-20
If you are wanting multiple desktops try right clicking on the top or bottom panel. Click add to panel. Then scroll down to Workspace Switcher. Highlight it then click the add button You should now see a couple boxes that will allow you to switch between virtual desktops. You may need to right click the box(s) and via preferences increase the columns or rows to get to 4 of them. Just play with them until you have the amount you want. \


If your looking for something else you may need to be more specific in what it is you want.

Oops just noticed you said Netbook Remix version. The above may not work on it. I have never tried the netbook version.

---

### Post by etdsbastar on 2010-07-20
right click the workspace switcher on your bottom taskbar (where 4 gray boxer appear) and select preferences.

see the screenshot, it openes the workspace window, adjust the preferences as desired. close the window.

Now increase the desktop number as desired, switch by clicking on the workspace buttons appeared.

Regards.

---

### Post by DrWeedBot on 2010-07-20
yhea i all ready tried that for some reason i cant add or remove any thing from the pannel

---

### Post by DrWeedBot on 2010-07-20
> **etdsbastar said:**
> right click the workspace switcher on your bottom taskbar (where 4 gray boxer appear) and select preferences.
 
see the screenshot, it openes the workspace window, adjust the preferences as desired. close the window.
 
Now increase the desktop number as desired, switch by clicking on the workspace buttons appeared.
 
Regards.
 
 
there is only one bar in UNR and its locked or something? so this wont work I need to know how to add the workspaces to the taskbar.

---

### Post by Brandel Valico on 2010-07-20
O'kay a quick google search found a solution on the forums.

Thanks to VeeDubb

---------------------------------------------------------------

VeeDubb
Way Too Much Ubuntu
 
Join Date: Mar 2008
Beans: 295
Ubuntu 10.04 Lucid Lynx
	
Re: Multiple Desktops with Ubuntu Netbook-Remix
HA! Got it.

If you want to stick with the full UNR launcher, and have nothing be different except multiple desktops, it's SUPER easy.

Open a terminal, (guake is an AWESOME terminal for a netbook by the way) and enter

Code:

gconf-editor

navigate down to apps>metacity>general>num_workspaces

And change the value from 1 to 2 (or however many you want)

Log out and back in, and bam! You can switch workspaces with ctrl-alt-left and ctrl-alt-right

No messing with full gnome, no having to deal with window title bars when maximized. No buggy and crash prone 2-d launcher, no wasting resources on compiz. Just two desktops with a launcher on each.
__________________
[http://StephenMichaelPhotography.com](http://StephenMichaelPhotography.com)
Last edited by VeeDubb; May 10th, 2010 at 06:03 AM..

---

### Post by DrWeedBot on 2010-07-20
Thanx will try this

---

### Post by kerry_s on 2010-07-20
if you add more desktops, you might want to disable single instance mode.

---

