---
title: "Gnome Window Decoration Button Placement"
date: 2006-05-23
forum: General Help
---

### Post by xtacocorex on 2006-05-23
Is it possible to configure the location of the window decoration buttons in Gnome like you can for kwin in KDE?

---

### Post by byen on 2006-05-24
I know this has been answered at the IRC channel (#ubuntuforums) but I would prefer to answer to this anyways, just incase someone looks for a similar answer:

To change the Window decorations i.e the placement of the minimize, maximize and the close button on a window in gnome please do the following:

Step1: Alt+ F2 (this will bring a run dialog window)
Step2: Enter: gconf-editor      (and hit the RUN button)
Step 3: You will now get a Configuration Editor Window . Please follow the following directory path: apps>metacity>general>button_layout (in the options window) and change the layout/sequence as you please.
Step 4: Restart Gnome 

To the best of my knowledge this should work. If it does not... let us know and we can dig around a little more. 
Hope it helps! Goodluck!
~byen

---

### Post by xtacocorex on 2006-05-24
byen, thanks again for the help.

EDIT: I got bored waiting to go to work, so I tried it out and it works perfectly.

---

### Post by byen on 2006-05-24
Cool! Glad to know it worked! :D Yeah I tried this too last night and looks like the changes you make take effect immediately too :P SO no need to restart gnome after making the changes :)

---

### Post by LT1Caprice57L on 2007-09-30
k guys.  I'm running Feisty and I cannot get this trick to work.  I've searched until I broke the search function and I can't seem to find an answer for this problem, either :(

EDIT:// just kidding.  apparently it just randomly decided to work...

in any event, I can now get my OSX themes to work right :D

---

