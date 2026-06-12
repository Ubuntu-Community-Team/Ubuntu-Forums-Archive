---
title: "I dun good'd up my X11 Mouse Theme"
date: 2010-08-26
forum: General Help
---

### Post by Zeenomorph on 2010-08-26
I just upgraded to Ubuntu 10.04, and was doing some visual tweaking.  One of the things I was doing was changing my mouse.  I was having trouble so I played trying to get it to work.  I've since found what the problem was here;

[http://ubuntuforums.org/showthread.php?t=1467129&highlight=mouse+theme+location](http://ubuntuforums.org/showthread.php?t=1467129&highlight=mouse+theme+location)

But when I was trying to fix it, I installed bunch of other themes and tried them as well.  When I did this I lost the theme that I wanted from the pointer menu.  Thinking that maybe there was a limit to the number of X-11 mouse themes allowed I deleted all the ones that I had installed, and tried to install the theme I wanted again.  

The issue seems to be that I can't install this theme again.  The error window says "Failed.  Can't move directory over directory".  I assume that the computer made a copy of the file *somewhere*.  I just can't find where.  I tried the home directory and ctrl + h but I can't see anything there.  

Any tips on how I can install this theme that I have already installed?

---

### Post by DavidOfLondon on 2010-08-26
You'll hate me for saying this but you'll be grateful at a later date :)

When you change your themes ALWAYS save them. If you use compiz it will give you this option on the left side of the screen. To be perfectly certain, save it to a USB stick. Changing themes often creates conflicts which wipe out your preferences.

I generally avoid using the terminal to look for anything and prefer the installed explorer. Use that or type "browser" into the Software Center and find one you like the sound of. Finding files on Linux is not currently that user friendly but is improving. Did you try the software center Installed Apps bar to see if the theme packages are still registered as installed? 

Oddly, sometimes using the Synaptics Package Manager locates installs that the Software Center can't see.

---

### Post by Zeenomorph on 2010-08-26
I figure if I can just find where my x-11 theme is saved I can sudo rm it.  Then I could install it fresh.  At this point it still thinks it's installed, but I can't access it, or reinstall it -- until I can get rid of the evidence.  

/sigh

---

### Post by DavidOfLondon on 2010-08-26
It's to do with the file structures. I still get pissed off at how difficult it is to find stuff but that's nearly always because I didn't make a note of where something was installing to at the time, etc.

In the terminal there are loads of ways to search, as you know, but the only one that searches the whole damned this is the command "locate" - I used it earlier today when the others all failed and "Hey Presto!" it found every file containing the word i searched for.

So open a terminal and type in "locate x-11".

Let me know how you get on.

David

---

