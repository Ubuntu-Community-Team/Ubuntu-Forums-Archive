---
title: "Creating an executeable script, for startup.  Wacom Tablet.  Help?"
date: 2011-11-12
forum: General Help
---

### Post by kaytalyst on 2011-11-12
First time poster, so my apologies if I haven't chosen the right place to do this.  Also a bit of a Linux noob, though I ran Jaunty for a year a while back.  

I've spent 8 or 9 hours now getting my wacom tablet set up, and learning the basics of the code lines that I'm running to get the damn thing working.   All I need now (finally)  is to create an executable startup script to rotate the thing to accomodate my left handed-ness, so I don't have to type this every time the comp restarts.  

I know the commands that I need (I've tested them)  are
[B]
xsetwacom set "Wacom BambooPT 2FG 4x5 Pen stylus" rotate half 

xsetwacom set "Wacom BambooPT 2FG 4x5 Pen eraser" rotate half

xsetwacom set "Wacom BambooPT 2FG 4x5 Finger pad" rotate half[/B]


After over an hour of searching, I'm at a loss on how to set this up in a script.  Though I set one up to toggle the touch, the script was already written.  

This is all I understand to be a commonality in the scripts  #!/bin/bash 


Any one have suggestions, or can point me to a more general thread/post/resource for creating and/or understanding the requirements for a script?

Edit: Also using Maverick 10.10

---

### Post by Favux on 2011-11-12
Hi kaytalyst,

Welcome to Ubuntu forums!

Instructions for setting up a script are in part IV. of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") along with attached sample scripts.

See also the Linux Wacom Project's mediawiki HOWTO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)
For example:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)

---

### Post by kaytalyst on 2011-11-12
Thank you [Favux]("http://ubuntuforums.org/member.php?u=699990") 

I swear I'd read those posts a hundred times.  I think I may have been over complicating it a *bunch.*    Thanks a million for pointing me to the right parts!  

All tested and set-up.  Best part, not only is the tablet finally working...but I know how to write scripts and set them for start up now!!

I *bow to you*  For setting up that wonderfully detailed thread, and doubly so for so politely pointing me to what you'd already said.

---

