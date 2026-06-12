---
title: "Setting keybindings and default menus ?"
date: 2010-09-04
forum: General Help
---

### Post by nagaprathyush on 2010-09-04
Hii again! Am hoping to find a solution for my problem here, in order to make my ubuntu nearly perfect :D
I used to have gnome-desktop-utils(gdu?) and evolution as my defaults  for screen shots, file search, dictionary etcetera and email client, until yesterday when I uninstalled them. I chose to use the screen-shot plugin in  compiz-configuration-settings-manager(ccsm) for screen-shots, artha for offline dictionary, beagled for file search and thunderbird for email and so  I felt there was no need of gdu and evolution. 

**Issue:**
    Now, the issue is that I did not know that I had to hold the super button and drag the mouse(left) to take a screenshot (which is good in its own way, of course!). I thought just the click of left mouse+super button would take the screenshot of entire screenshot. The main disadvantage of mouse dragging is that I can not take the screenshots of highlighted menus when needed :( 
    So, I was wondering if I could define a keybinding "Print" probably to take me a screenshot of the whole screen and a window (lets keep it simple and assume for now that the window is maximized ;)) screenshot as "Alt+Print" using ccsm screenshot plugin. 
[IMG]http://img28.imageshack.us/img28/9524/screenshot3va.png[/IMG]
The above pic shows the ccsm plugin gives me very limited options for a screenshot. I know that button 1,2,3 means mouse clicks, but I have no idea whatsoever of the rest buttons 4-9 :o

I even tried installing "xdotool" to write a simple .sh script to take me a screenshot of the whole screen, but even then I need to drag the mouse along (as i havent changed the ccsm plugin screenshot hotkey), which means I wont be able to take the screenshots of highlighted drop down menus. 
[IMG]http://img97.imageshack.us/img97/1599/screenshot4w.png[/IMG]
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[IMG]http://img267.imageshack.us/img267/9702/screenshot5jc.png[/IMG]
Then I went to gconf-editor, apps, metacity, global keybindings and saw that the default screenshot(gdu's?) are set there and also there are some empty slots(shown as disabled) for new user defined commands(run_command_1 to 9) may be. Now am puzzled, what if I can give a new command(.sh script in the previous paragraph) there to invoke ccsm to take a screenshot instead of the non-existant gdu screenshot plugin.

**Queries:**
1.How do I edit the ccsm plugin hotkey to just a single key(print button on my keyboard), so I can take screenshots of highlighted menus? ie., what are the buttons 4 to 9 in attachment 1? 
2. How can I define a new keybinding at the gconf(if its possible, may be) so that I can use my xdotool script to take a screenshot using ccsm plugin? Similarly how can I define a keybiding so that thunderbird opens up(I presume my mutimedia keyboard's mail button is trying to get the non-existent evolution) ?

---

### Post by nagaprathyush on 2010-09-04
Should I take away the pics and post just the image links instead ? I am afraid these pics clutter the thread:o

---

