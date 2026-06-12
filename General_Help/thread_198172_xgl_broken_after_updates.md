---
title: "xgl broken after updates"
date: 2006-06-16
forum: General Help
---

### Post by starkes on 2006-06-16
seems my xgl has been broken since applying 70+ updates through the update manager.


Basically, what happens, is that i select my "xgl-gnome" session, and then it loads up in a way that *looks* like its going to work (loads up with grey background and X symbol before splash screen, as it did before) but when it does finally load, I will either be missing my window decorations, or that AND my gnome panels.

Also, when i press alt+ctrl and click to rotate the cube, it does not rotate, it just makes a selection box. So it seems like compiz is not working whatsoever.

I have removed and then installed the compiz and compiz-gnome packages, which i believe are the CVS version, and i still have the same problem. My configuration, as far as i know, is the same as the old configuration.

this is the tutorial i used to set up my xgl to use a seperate session (i would rather not have xgl if i couldnt do it this way):
[http://www.ubuntuforums.org/showthread.php?t=174233](http://www.ubuntuforums.org/showthread.php?t=174233)

this is where i got the info on using the CVS build:
[http://ubuntuforums.org/showthread.php?t=148860](http://ubuntuforums.org/showthread.php?t=148860)

I am wondering... has anyone had this problem? or can anyone with a working xgl/compiz tell me what plugins they have in their gconf-editor, and in what order? I'm thinking maybe a plugin went missing or something, because I can't see anything else wrong...

---

### Post by Bokonon on 2006-06-16
I have a similar install on my laptop/nVidia, but it works for me.  Things are sluggish, so I expect some further patches.

I am pretty sure I saw a new nVidia driver/module in the updates, so the compiz/Xgl people probably have to work a bit to get things working smoothly again.  

Does it work with the old kernel (2.6.15-23)??

---

### Post by starkes on 2006-06-16
i'm using an ati card though

but i do have the drivers set up properly, they work just as they did when xgl worked before.

you bring up a good point though, i'm going to check out the old kernel and see if it still works on that, and then ill come back and post what happened.

---

### Post by djsamsel on 2006-06-16
i was having a similar problem. i can't tell you why this worked for fixing it, but it did. start up in safety mode and at the root run

sudo dpkg-reconfigure xserver-xorg

and select the ati driver, go through the rest of the process selecting the standard selections. when complete type exit and it will boot to a 640X480 login screen. boot into gnome and open a terminal and again run 

sudo dpkg-reconfigure xserver-xorg

this time choosing the fglrx driver. once complete, close the terminal, hit ctr-alt-backspace and you should be back at your normal session booter. login into to your xgl account and it should work. hope it helps!

---

