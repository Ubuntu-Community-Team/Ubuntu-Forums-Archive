---
title: "Maximis/minimise Windows"
date: 2010-01-20
forum: General Help
---

### Post by cozski on 2010-01-20
Hey... I dont have the usual maximise/minimise icons when I have a window/application open which is pretty problematic if I open multiple windows as I can only view the one on top. I'm using Netbook Remix... any ideas? Thanks :)

---

### Post by lotharmat on 2010-01-20
> **cozski said:**
> Hey... I dont have the usual maximise/minimise icons when I have a window/application open which is pretty problematic if I open multiple windows as I can only view the one on top. I'm using Netbook Remix... any ideas? Thanks :)

I'm pretty sure that this is a UNR feature!

I can't for the life of me remember where though.

---

### Post by anaconda on 2010-01-20
That is one reason I changed to normal ubuntu on my netbook..

However you can do it: 
right-click on the top panel of the window, and select minimize, or maximize as you like.


You can also try if the F11 key work for maximizing and minimizing too??

---

### Post by cozski on 2010-01-20
When I initially installed UNR the windows had the usual icons sitting in the top left corner... I think after I've been dicking about with the settings using Compiz I may have changed it... it's very annoying... everything opens maximised and I cant see underneath without closing the application :( Right-clicking on the top of an open window doesn't have any affect.

---

### Post by cozski on 2010-01-24
Well this is just ridiculous... I simply do have an option to maximise and minimise windows... I cant close a window without shutting down my system and re-starting if the window opens up fully maximised (which they tend to do alot). Surely this cant be how UNR is presented... it's virtually impossible to operate. Help, please!

---

### Post by anaconda on 2010-01-24
Alt-F4 closes a window.

And the right-clicking thing works on my system... strange..

---

### Post by cozski on 2010-01-24
Alt-F4 does work, but this is only helpful if I need to close a window... no good for minimising and bringing back up... and the right-click functionality doesn't respond. When I initially installed it an open window/program had a tab system similar to the one used in firefox running across the top panel with the usual 3 buttons for minimis, restore & close, but now it doesn't do that :(

---

### Post by fooman on 2010-01-24
you do have a top panel,  correct?  ...do you not also have little boxes/icons in that top panel that represent each open window? ...you should be able to right-click on those to minimize/maximize the windows.

if you *do not* see those boxes/icons for the open windows...you may be missing the "window-picker".  to add it to the panel,  just right-click on an empty space within the top panel (window-picker is usually placed in the left corner,  so that may be the area you want to right-click in) and choose "window picker" from the drop-down list that appears.

that should give you an icon near the left corner of the top panel for each open window/app that you have.  you can right-click on these icons to minimize/maximize.

hope that helps.

---

### Post by cozski on 2010-01-24
:D Thank you my man! This has resolved the problem, I think! You've no idea how many Naps I missed on Betfair because I couldn't get back to my browser! Must have cost me a few hundred quid today alone :( Still, back up & running. Thanks again :)

---

### Post by fooman on 2010-01-24
your welcome,  glad it worked.  btw,  you can also disable the whole "maximus" thing if you do not like it....that way you will have the normal bar at the top of each open window with the 3 little boxes for minimize/unmaximize/maximize in the top right corner.

to disable maximus,  go to main menu > system > preferences > startup applications....and uncheck "maximus window management".

---

### Post by cozski on 2010-01-24
Thanks for that... I'll give it a try :)

---

### Post by darrellsmith on 2010-01-27
I too am a power user with Unix/Solaris/Linux professional experience starting from the early 1970's. I am amazed at how well the Starling works. I installed my usuals: gvim, ssh, sshfs, vifm, autojump. This was to get the basic command line stuff and network connectivity going. Then the gui intensive apps and games AND Polytonic Greek and Hebrew support. It all worked fantastically well. 



The only problem was with maximus. I like having windows that I control. I like small windows.  See bug report: [https://bugs.launchpad.net/maximus/+bug/362301](https://bugs.launchpad.net/maximus/+bug/362301)
 

I tried changing preferences and disabling it from startup -- TO NO AVAIL. This is what finally worked (via the bash super user command line):



which maximus -- to find the location of the binary file (/usr/bin)
cd /usr/bin
chmod a-x maximus
 

This forced it to be unexecutable. So no more problems with those full screen windows. It was very annoying.

---

