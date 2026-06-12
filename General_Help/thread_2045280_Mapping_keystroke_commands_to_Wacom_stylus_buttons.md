---
title: "Mapping keystroke commands to Wacom stylus buttons"
date: 2012-08-20
forum: General Help
---

### Post by SKyPH3R on 2012-08-20
Not sure if I've missed something in plain sight or if this is just isn't an available feature, but I cannot figure out how to map the buttons on my Wacom Intuos 3 tablet's stylus to keystrokes. I can map keystrokes to my tablet's buttons, but not the stylus. In system settings, all I can see for the stylus are preset options like scroll directions, mouse buttons and "back and forward" which are useless to me. 

I'm making an effort to do my illustrative work in Ubuntu with GIMP instead of OS X with Photoshop. This is the only real annoyance left that I haven't figured out. Ideally I want to assign the two buttons on my Intuos 3 stylus (the ones on which I place my index finger) to Undo and Redo so I can rapidly flip through brush stroke attempts and draw with the same hand. 

Any pointers would be great, so I could set up any friend's workstation's who would be interested in trying these programs. Thank you.

---

### Post by Favux on 2012-08-20
Hi SKyPH3R,

Welcome to Ubuntu forums!


Far be it for me to comment on someone else's workflow but I always thought middle click for grab and right click for the menu were pretty reasonable in Gimp and Inkscape and what not.

Are you saying that you tried the xsetwacom commands for the stylus buttons and that didn't work or that the Gnome Wacom tablet gui doesn't offer a way to set key actions to them like it does for the pad buttons (ExpressKeys)?

If the former what exactly did your xsetwacom commands look like?  Either way post the output of **xinput list** in a terminal so we have the correct "device name" for the xsetwacom commands.

---

### Post by SKyPH3R on 2012-08-21
Maybe I should suspend this thread and do some further reading on xsetwacom. I had thought it was the underlying program for the Gnome Wacom Tablet gui. I'm fairly new to command line. I should have a response by tomorrow night. Thank you for the quick reply.

---

### Post by Favux on 2012-08-21
OK, if that's what you want.

The manual is available by entering in a terminal **man xsetwacom**.

And a couple of relevant Linux Wacom Project mediawiki pages:
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom)
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)

---

### Post by SKyPH3R on 2012-08-21
Thank you for the links.
It seems I'm not comprehending what I'm reading enough to help you help me. Is it true that any changes I make using xsetwacom will be reversed upon the shutdown of my computer or disconnection of my tablet? 

If what I wish to do can be accomplished through the Gnome Wacom Tablet gui (I suppose not) I'd prefer it. It is a basic feature in the OS X Wacom driver. I know enough to not expect Ubuntu to be a mere OS X substitute, but I'll simply adjust my work flow if this method doesn't prove to be very convenient. I'm mostly curious, so no pressure.

What would this... list of commands resemble? 

xsetwacom
xsetwacom devices list

I see 
Wacom Intuos3 9x12 stylus           id: 8    type: STYLUS   
in this list

xsetwacom list modifiers
These seem to be keys to which I can set my buttons and then set GIMP actions to.
Say f1 and f2 to my stylus buttons then tell GIMP to change undo and redo from what they are to f1 and f2?

And perhaps xsetwacom shell is used in part to make the actual changes?

---

