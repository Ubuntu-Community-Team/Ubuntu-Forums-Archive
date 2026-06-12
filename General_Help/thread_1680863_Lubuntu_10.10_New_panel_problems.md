---
title: "Lubuntu 10.10: New panel problems"
date: 2011-02-03
forum: General Help
---

### Post by t0p on 2011-02-03
Messing around with the settings of my bottom panel, I ended up making a right pig's ear of the thing.  So I decided to just delete that panel and create a new one, rather than try to fix all the problems I'd made.  But now I'm having a few problems with setting up the new panel:

1. I've got "Network Status Monitor" and "Network Connections" on my new panel. Network Status Monitor was born dealing with the *eth0* interface. But when I wish to use a different interface (eg *wlan0*) I have to go into Network Connections" and manually tell the thing what I wanted to do; whereas the original network manager tool on my old panel did this automagically.

2. As I have added stuff to my new panel (eg application launchers, File Manager, clock) it's all appearing on the panel in the order of my creating them.  There doesn't seem to be any way to move the icons around.  When using Ubuntu, with its default Gnome, I could move panel items around, by right-clicking them, unchecking "lock to panel" (if required) then clicking on "Move".  Is there any way to move panel items like that in Lubuntu?

3.  I don't like the icons that appear when I add a new item to the panel.  For instance, the "Menu" icon on the original panel was a nifty-looking icon that I think may be the Lubuntu icon. But on my new panel, the Menu icon looks like a computer and monitor.  How do I go about changing the icons of panel items in Lubuntu?

4. When I minimize a running application, no icon for it appears on the bottom panel. To get back to a minimized window, I have to right-click on the desktop, and go (for instance) **Desktops > Desktop 1 > whatever the Firefox web page title is called**. That is a very unsatisfactory method to use.  How can I set up the original behaviour.  How can I restore the previous minimize/restore behaviour? ie when I minimize a window it makes a little entry on the panel - when I want to maximize it again I just click on the apprpriate part on the panel.  This one is a big problem, as it makes switching from one running app or window to another *very* fiddly.  I don't like fiddliness.  You might have assumed that this could be solved by right-clicking on the panel and going to "Panel Settings".  That's what I assumed.  One more lesson in why you should never assume anything, I suppose.  *Gaahhhh!!!*
**EDIT:** Never mind about 4.  I sussed it out - what I needed to add was **Task bar > Window list**.  But the other stuff is still in dire need of attention/intervention.  Especially the thing about moving stuff around on the panel.  I really really want to be able to move stuff around on the panel!
Cheers.

---

### Post by t0p on 2011-02-04
*bump*

The major problem:  In Gnome (Ubuntu) it is possible to move icons/launchers around on the panel by right-clicking on the icon and selecting "Move".  On my Lubuntu (LXDE?) panel, there doesn't seem to be any "Move" option.  So, do I have to delete everything on the panel, then re-add them in the correct order?  Do I really have to go through all that rigmarole just to have my panel the way I like it?

---

### Post by SteveDee on 2011-02-06
I won't attempt to unravel the mess you are in, but I find the LXDE panel much better for my needs than Gnome. Here are some brief notes on customisation.

Right click on the panel and select Panel Settings.

 - Select the "Panel Applets" tab and tick the 3 "Spacer" tick boxes. This gives you logical groups of icons spaced out on the panel (or if it doesn't, you can highlight a spacer in this list and move it up or down until you are happy!).

 - Highlight "Application Launch Bar" and click edit. This displays the Apps Launch Bar dialog so you can now add/remove apps and change their position within the apps group using up/down keys.

 - Back in Panel Preferences/Applets, highlight "Task Bar" and select Edit. Tick all the tick boxes. I especially like "Show windows from all desktops" as I use 4 desktops and keep losing things when running on Gnome.

 - Back in Panel Preferences/Applets click Add and select "Desktop Number...". Now highlight it in the list and move it up so its next to Desktop Pager. With it still highlighted select edit. Untick "Display desktop names"

Anything else in the panel can be added/deleted or moved from the Panel Preferences/Applets dialog. You can even replace the dreadful "start" icon with something better (you have to make it yourself) by highlighting "Menu" (in Panel Applets) and selecting edit.

I hope this helps.

---

### Post by Neosano on 2011-02-08
Haha, I'm sorry, but I can't understand how can somebody be that blind...
I'm using Lubuntu 10.10.

1) Double-click on it, press down arrow and choose Wlan0 or anything you want. This setting must stay still after restart. If it doesn't work, try clicking EDIT button in Panel Applets tab(while network manager is selected) and then just type wlan0 to "Interface to monitor" thing.

2) Yeah, Panel settings/Panel applets, click on any item you want to move and then click UP or DOWN buttons. 

3) Right click on the Menu, click "Menu" Settings.
I screwed it up too, can't find the old icon :<
**GUYS, please do the same thing and tell us the path to default menu icon!**

4) Task bar. (you already found it)

---

### Post by SteveDee on 2011-02-08
> **Neosano said:**
> GUYS, please do the same thing and tell us the path to default menu icon!

For Lubuntu 10.10: /usr/share/lubuntu/images/

For Ubuntu + LXDE: /usr/share/lxde/images/

---

### Post by Neosano on 2011-02-08
Yeah! Thank you.

---

