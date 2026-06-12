---
title: "Quick launch for songbird"
date: 2009-08-16
forum: General Help
---

### Post by gotanothergrot on 2009-08-16
I want to put songbird in the applications to launch it from there, without navigating through the files.

thanks

---

### Post by sigixv on 2009-08-16
presuming you are using gnome and referring to top bar menu:

Right click it and there should be something like "modify menus" (not using english version here)
Select where you want it and press "new item" in the right colum
Add the songbird launcher

For such popular applications it's often possible to use a .deb install file. Just google it or take a look on [URL="http://ubuntuforums.org/www.getdeb.net/"]www.getdeb.net/
[/URL]

---

### Post by lariosa42 on 2009-08-16
sigixv has some good advice, but here is the English version (for Ubuntu 9.04):

-Right click the top menu
-Select "Add to Panel..."

Now you have two choices, "Custom Application Launcher" or "Application Launcher."  

If you can already find Songbird under your regular "Applications" menu (which means you probably installed it from a .deb), just use the "Application Launcher" option and select Songbird from the menu.

If you can't launch Songbird from the Applications menu (which is probably the case), open up a terminal (Applications --> Accessories --> Terminal) and type:
```
which songbird
```
This will tell you **which** command Ubuntu uses to launch Songbird.  (Note: [FONT="Courier New"]which[/FONT] is case sensitive, so you might have to type [FONT="Courier New"]which Songbird[/FONT] or something.  It should give you output which is something like this:
```
/usr/bin/songbird
```
Now all you need to do is to pick "Custom Application Launcher" in the "Add to Panel" menu, and enter [FONT="Courier New"]/usr/bin/songbird[/FONT] (or whatever the output was from [FONT="Courier New"]which songbird[/FONT].) into the "Command" section.  You can name it whatever you want.  (Note: "Type" should be set to "Application," not "Application in Terminal.")

I hope that helps!

---

### Post by sigixv on 2009-08-16
My how-to was merely for placing it in the gnome-menu (as under the "applications" tab)
;-)

---

### Post by gotanothergrot on 2009-08-16
Code 'which songbird' didn't work in terminal so I tried the  putting the path in the launcher which something is I'm not doing properly,  see attachment.

past midnight will check-back later..

thanks

---

### Post by sigixv on 2009-08-16
You forgot to put something in the Name box... (this is the text how it will be displayed in the menu)
Also, you might want to set the proper icon for songbird if you want to put it in your dock later on...

---

