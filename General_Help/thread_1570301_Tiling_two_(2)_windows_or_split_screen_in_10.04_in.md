---
title: "Tiling two (2) windows or split screen in 10.04 in gnome"
date: 2010-09-08
forum: General Help
---

### Post by mfrag on 2010-09-08
Hey all,

Thought I'd share something neat I just found.  I've been struggling in gnome for some time to quickly split one screen in two so that two windows appear fully on the screen; one using the left hand of the screen and the other the right half.  

I've used tiling window managers which do this easily and some even do it automatically.  Ratpoison and ion work well for instance. But over the years I've run into other problems using these different window managers.  I have had trouble with ratpoison getting usb drives to be read when plugged in for instance.  Answers to some of my problems were difficult to find and usually where given for gnome/metacity users which sometimes didn't help when I was using a different window manager which tiled nicely or by default.  Since most people seem to use Ubuntu out of the box with gnome and most help on the forums is aimed at these standard users I decided to switch to gnome and learn it.  While I will still use ratpoison on my older machines, I have come to really appreciate gnome and I use it on my beefier machines.

So, what is a quick way to tile two windows side by side?  x-tile will help!  You can find it at:

[http://www.giuspen.com/x-tile/]("http://www.giuspen.com/x-tile/")

Download the .deb file and let ubuntu install it for you. 

Next you will want to have open the two windows you would like to have side by side.  I for instance commonly have firefox open for online-banking and an open office spreadsheet open for my budgeting. I like to have these windows open side by side (not in different workspaces as I need to see both at the same time).  I also like to have vim open in a terminal where I'm latexing and xdvi open in another window.  I like to have these side by side for reverse searching in the .tex document (again, different workspaces doesn't help here).  Anyhow, I'm sure you have different windows you would like to have open side by side or maybe three even.  So get the two or three or whatever windows open you would like to tile.  

Next open x-tile by going to:

Applications -> Accessories -> X-tile

First you have to filter out x-nautilis-desktop (unless you want part of the desktop viewable).  To do this click on:

File->Filter-> +

Then select nautilis, click ok, and then close the filter window.  Next select the windows you want tiled and then select the tiling pattern you like (I like the second option to have them side by side).  There are several predefined options to choose from and a custom option as well.  This should tile the windows for you as you like.

Now to create a shortcut. Goto:

System -> Preferences -> Keyboard Shortcuts 

Scroll to the bottom and under Custom Shortcuts click the Add button.  Name it whatever you like and give the appropriate command.  I used:

x-tile --tile-all-horizontally

for the command.  The different commands are given at the bottom of the x-tile link above.  Next give it a shortcut like Ctrl-Alt-S or something that suits you.  Now whenever you have the two windows open you want side by side simply type in the shortcut and you don't have to bother with resizing things like you want them manually with the mouse.

Hope this helps someone.  For those with more knowledge than I, please offer your suggestions.

---

### Post by DrMilo on 2010-10-07
Awesome! I have been looking for this literally for years! 
Thank you!

---

### Post by mfrag on 2010-10-07
> **DrMilo said:**
> Awesome! I have been looking for this literally for years! 
Thank you!

Glad you found it useful!

---

### Post by krakra on 2010-11-09
Thank you. With this Ubuntu keeps getting better.

---

### Post by dino99 on 2010-11-09
hey, many thanks

good catch, ive spent lot of time to find such app but did not succeed, but you get it :)

---

### Post by pagemaker on 2010-12-05
Thanks for this great little program! Very useful!

---

### Post by mfrag on 2010-12-06
Glad this has helped a few.  I'm particularly glad I posted it because on a recent reinstall I had to go back and set this up again. I would not have remembered my steps easily without my post!  I'd like to see x-tile get added to the distribution myself.

---

### Post by blur xc on 2010-12-06
I've used compiz grid and maximumize plugins to accomplish this...  When I'm playing around with python or bash scripting I'll normally have two terminal windows open, and a pdf, iether the python e-book or bash scripting book I'm referencing tiled on the screen.

BM

---

### Post by ToniMe on 2011-04-06
Very useful! Thank you! I have been trying to figure this out ever since I started to work with ubuntu. I am on Lucid Lynx now and x-tile WORKS just fine!

---

### Post by sjdude on 2012-09-06
You might want to check the options on x-tile as they appear to have changed. The option in the example given for "tiling all windows horizontally" has changed to simply "h" on the command line. Otherwise, this is so excellent I wonder why it isn't already part of gnome.

---

