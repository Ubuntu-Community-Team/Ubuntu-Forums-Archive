---
title: "Karmic Applications&gt;Games Not Changing"
date: 2010-01-06
forum: General Help
---

### Post by fatecaresx13 on 2010-01-06
**Hi All,**

I've recently installed Karmic on my desktop and I've been tweaking everything to my liking.  I was recently attempting to clean out all the applications I don't use and I wanted to remove all the games from the list except for one game which I play often.  After going into *System>Preferences>Main Menu* and unchecking everything except the one game I want to show I noticed the games remain unmodified in the *Applications>Games* menu.  Any ideas as to why?

Thanks in advance,
Anthony

---

### Post by mocoloco on 2010-01-06
You might be clicking on "revert" instead of close.  New users think they need to always "apply" changes, but in Gnome (the Ubuntu interface) most changes happen immediately.  So when you're done you just click "close".  The "revert" button puts things back the way they were.

---

### Post by fatecaresx13 on 2010-01-06
> **mocoloco said:**
> You might be clicking on "revert" instead of close.  New users think they need to always "apply" changes, but in Gnome (the Ubuntu interface) most changes happen immediately.  So when you're done you just click "close".  The "revert" button puts things back the way they were.

Although I was very tempted to click some type of apply before I hit close I did not.  However I'm going to revert and retry to uncheck all those games again to see if I can fix the issue.

---

### Post by fatecaresx13 on 2010-01-06
No go.  I should note that I can edit **everything** except the Games section. :confused:

---

### Post by mocoloco on 2010-01-06
Wow, strange.  Lets try this. Open your home folder, then press Ctrl+H to enable showing hidden files.  In your home folder open .local (yes is starts with a dot, all hidden files/folders do in Linux), then share, then applications.  In that folder go ahead and delete everything.  

A quick explaination: the files for the menu entries are system controlled and you can't actually remove them as as regular user, instead when regular users make changes they're stored in here, and anything in these files overrides the global menu settings, including disabling an item, renaming it, moving it to another category etc.

Once you clear it out you should be able to start over with the menu editor.  See if that makes any difference.

---

### Post by fatecaresx13 on 2010-01-06
> **mocoloco said:**
> Wow, strange.  Lets try this. Open your home folder, then press Ctrl+H to enable showing hidden files.  In your home folder open .local (yes is starts with a dot, all hidden files/folders do in Linux), then share, then applications.  In that folder go ahead and delete everything.  

A quick explaination: the files for the menu entries are system controlled and you can't actually remove them as as regular user, instead when regular users make changes they're stored in here, and anything in these files overrides the global menu settings, including disabling an item, renaming it, moving it to another category etc.

Once you clear it out you should be able to start over with the menu editor.  See if that makes any difference.

**rm -rf .local/share/applications/**


And the menu looks like new but in *System>Preferences>Main Menu* I noticed nothing is checked under *Games*

---

### Post by SchizmWolf on 2010-01-06
Have you tried using alacarte to get rid of the icons for games you don't use?

---

### Post by fatecaresx13 on 2010-01-06
Ha, yeah.  That's what I'm navigating to from *System>Preferences>Main Menu*.  Still no fix.  Also, when I check the games the check will refresh and uncheck itself even though the icons are clearly still there.  Something is broken. :/

---

### Post by fatecaresx13 on 2010-01-06
Sorry to bump but does anyone have any idea how to clean or revert the Applications list so I can try this again?

Thanks,
Anthony

---

### Post by mocoloco on 2010-01-06
My next suggestion would be to create a new user and see if that user has the same problem, to know if it's a system problem or something specific to your user only.

---

### Post by fatecaresx13 on 2010-01-07
New user "apptest" has the same issue. :(

Anthony

---

### Post by mocoloco on 2010-01-08
OK, I feel like an idiot.  I went today to disable some games from the menu on my wife's computer (tali, robots, does anybody play those?) and lo and behold, same issue.  So I went back to my own machine and tried the same thing.  Same issue.  In other words it looks like a bug to me.  And I have to say shame on me for giving suggestions but never actually trying to duplicate it myself! (and unless you tried it too, shame on the rest of y'all :))

So it looks like the bug is that only for the games menu no .desktop files are put in ~/.local/share/applications.  There are however changes made to ~/.config/menus/applications.menu, as there should be.  My guess is it came about because of the addition of the sub-menus under the games menu, somebody missed something.  I've searched on launchpad and not found any report of this.  Before we submit one, anyone else want to confirm that this is not isolated to fatecaresx13 and me?

---

