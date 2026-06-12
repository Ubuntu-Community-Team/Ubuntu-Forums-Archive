---
title: "How can I get Terminal back into Apps -&gt; Accessories menu?"
date: 2010-01-30
forum: General Help
---

### Post by watchpocket on 2010-01-30
I was having some trouble with the Terminal so  I removed and re-installed gnome-terminal, gnome-terminal-data, and termlauncher applet.

(The trouble was that terminal was opening itself again and again infinitely, due, I think, to a script I was calling the terminal command).

As a result Terminal is no longer in the Applications -> Accessories menu.  (I've probably hosed my terminal configs as well.)

Also, terminal now only launches for a second, then disappears.

Anyone know how I might get it to launch successfully, and get it back into the A -> A menu?

---

### Post by NightwishFan on 2010-01-30
If it is merely hidden, you can show the menu editor by pressing alt+f2 and typing:
```
alacarte
```

If the terminal is not working, you can use xterm for now, as it is installed in Ubuntu.

---

### Post by watchpocket on 2010-01-30
Thank you muchly,  I was able to put it back in using the alacate command.

However I can't get Terminal to launch -- it just blinks.

I am using xterm but it's my first time.  Background is blinding white and font is tiny.  How can I change that?

---

### Post by NightwishFan on 2010-01-30
I am not sure, it is a very simple application. Changing how it looks should be possible, though it might involve editing text files. Try looking up some documentation for it. My point was, you can try to run the other terminal from the Xterm to see what is wrong.
```
gnome-terminal
```

---

### Post by watchpocket on 2010-01-30
> **NightwishFan said:**
>  . . . you can try to run the other terminal from the Xterm to see what is wrong.

Oh I've done that, terminal just blinks & exits.  And I've been looking through xterm man, I'll keep looking.

I'm also trying to wend my way through "locate gnome-terminal" and everything it shows.  Terminal is also a pretty basic app, but it just ain't coming up.

Looking through this list of files, I'm pretty lost as to where to look to make a fix.  The script-call may still be in the Terminal launch command, but I can't get at that command to look at or change it.

---

### Post by warfacegod on 2010-01-30
> **watchpocket said:**
> Oh I've done that, terminal just blinks & exits.  And I've been looking through xterm man, I'll keep looking.

I'm also trying to wend my way through "locate gnome-terminal" and everything it shows.  Terminal is also a pretty basic app, but it just ain't coming up.

Looking through this list of files, I'm pretty lost as to where to look to make a fix.  The script-call may still be in the Terminal launch command, but I can't get at that command to look at or change it.

You should be able to Right Click your menu button and select Edit Menus. From there you can add a check next to the Terminal. While you are in there, click properties, with the Terminal entry highlighted. That will show you the launch command.

---

### Post by watchpocket on 2010-01-30
Yes!  Thank you.  The command is simply "gnome-terminal".  ("Type" is set at "Application".)  

This stuff really requires imagination as much as anything else.  Answers are so elusive when you need them, but so often obvious after you have 'em. . . .

I wonder what anyone's starting point would be for troubleshooting why a friggin' terminal won't launch. . . .

---

### Post by warfacegod on 2010-01-30
> **watchpocket said:**
> Yes!  Thank you.  The command is simply "gnome-terminal".  ("Type" is set at "Application".)  

This stuff really requires imagination as much as anything else.  Answers are so elusive when you need them, but so often obvious after you have 'em. . . .

I wonder what anyone's starting point would be for troubleshooting why a friggin' terminal won't launch. . . .

Glad that helped. Try looking in your system logs. /var/somethingorother

---

### Post by watchpocket on 2010-01-31
Any more ideas from the group mind?  Half-baked ones welcome!

---

### Post by warfacegod on 2010-01-31
> **watchpocket said:**
> Any more ideas from the group mind?  Half-baked ones welcome!

If you like half-baked then put your computer in the oven and bake it for only half the time it would take to fully cook it.:P

---

### Post by watchpocket on 2010-01-31
> **warfacegod said:**
> If you like half-baked then put your computer in the oven and bake it for only half the time it would take to fully cook it.:P

Good idea, except it's working like I already did.  But what would you do if you were in my situation?  Right now I'm trying to look through gnome-terminal config files and logs in the log file viewer.  A bit lost in a forest of files, trying to figure out the right ones to examine.  And so on.

---

### Post by mechro on 2010-01-31
Try renaming .gconf/apps/gnome-terminal to .gconf/apps/copygnome-terminal or similar. Log out, log in and a new gnome-terminal folder will be created...

Whether this will work... I don't know.

---

### Post by warfacegod on 2010-01-31
> **watchpocket said:**
> Good idea, except it's working like I already did.  But what would you do if you were in my situation?  Right now I'm trying to look through gnome-terminal config files and logs in the log file viewer.  A bit lost in a forest of files, trying to figure out the right ones to examine.  And so on.

What I would do and what a normal person would do are not necessarily the same thing.

Try using Synaptic and Completely Removing:

gnome-terminal

&

gnome-terminal-data

Then install them again.

---

### Post by watchpocket on 2010-01-31
You have saved my life, mechro.  

This works.  Brings up a raw configureless terminal which I can easily (re)configure to taste.  I may try to put one of the old profile files back in to see how that works but will probably just reconfigure.

l would not have known what to do and was looking at everything in both .gconf/apps/gnome-terminal and .gconf/apps/gnome-terminal-launcher but wouldn't have known what to let regenerate.  I guess after a while you get a feel for these things.  Thank you!

(As for remove&reinstall, I'd just done that.  Copying away the .gconf files did the trick & thanks to all who responded my howls in the night.)

---

