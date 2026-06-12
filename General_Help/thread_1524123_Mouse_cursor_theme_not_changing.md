---
title: "Mouse cursor theme not changing"
date: 2010-07-04
forum: General Help
---

### Post by itsjareds on 2010-07-04
Hi, for some reason when I change my cursor theme to anything except DMZ-White (the default) on Ubuntu, the theme will not change even after a reboot. I only see the new theme when the cursor changes for certain things such as hovering over a link or hovering over a textbox. I also see the new cursor theme when I have the mouse inside a flash app. However, on the normal desktop or normal use I still see the old default cursor theme.

Any suggestions?

---

### Post by WorMzy on 2010-07-04
Using Compiz?

It's a fairly common problem if you are. Creating a new document at ~/.icons/default, calling it "index.theme" opening it with gedit (or equivalent) and putting the following content in it:
```

[Icon Theme]
Name = 
Comment = 
Example = 
Inherits = <NAME OF CURSOR THEME YOU WANT>

```
fixes it. You can put whatever you want after Name, Comment and Example, but make sure you put the exact name of the cursor theme after Inherits. Log out and back in, and it should display the cursor you want.

---

### Post by itsjareds on 2010-07-05
Thanks, that seemed to fix it :D stinks that I have to do that for every theme change. Do you know if a bug is already reported?

Before your response I found a way to do the same thing except system-wide for all users using this command:

```
sudo update-alternatives --config x-cursor-theme
```

Then choose the number of the theme you want to use.

---

