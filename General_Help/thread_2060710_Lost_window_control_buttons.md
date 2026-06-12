---
title: "Lost window control buttons"
date: 2012-09-20
forum: General Help
---

### Post by Unotforme on 2012-09-20
Help!

Not sure what has happened, but all my windows (apps) have lost the min/max/restore/quit buttons in the upper right (I can still drag the window around); I can't access any pull down menus with the mouse (that is to say when I click on a menu item the submenu shows but disappears when I try click on one); and the resize arrows for windows (when on the border of window) don't show up either. The default dock now stays behind any open apps, so I can't even access that..

I've been going thru settings but can't find anything to remedy the situation. I'm sure I hit a key combo to screw this up, but no idea what.

?...

---

### Post by daslinkard on 2012-09-20
What happens to the issue if you do the following:

```
unity --reset
```

---

### Post by Toz on 2012-09-20
Actually, if the op is using xubuntu, the proper command to restart the Xfce window manager is:
```
xfwm4 --replace
```

You might also need to issue a:
```
xfdesktop --reload
```
...if the first command doesn't restore all functionality.

---

### Post by oldos2er on 2012-09-21
Changed thread title.

---

### Post by Unotforme on 2012-09-22
No dice.

Regained some functionality, but still can't min/max or resize windows, some submenu options just don't work, either with keystrokes or mouse. I'm able to access terminal and found some help with xfce4 settings, but still can't get to where I was.

I've noticed the 'onboard' keyboard now loads up on default (like a starting app), but I don't see anywhere to disable it on boot; I can hide it, just can't disable. I've never noticed it before I started having issues. I have other users on this computer and they are not having any realted issues (that I know of).

---

### Post by Toz on 2012-09-22
Try clearing your saved sessions cache. 

First, logout and go to your first tty (Ctrl+Alt+F1) and log in to the text console. Then clear your cache by carefully issuing this command:
```
rm -rf $HOME/.cache/session
```

Go back to your giu (Ctrl+Alt+F7) and login again.

If you're still having problems, post back a copy of your ~/.xsession-errors file. Run this command:
```
pastebinit ~/.xsession-errors
```
...and post back the link that is generated.

---

### Post by Warprunner on 2012-09-22
I had a similar issue with the buttons moving to the left again, yesterday. I went to Gconf-Editor and they showed to the right. Strange. This all happened after an update.
Found a post about it. Changed things back.
Your issue is more intense but maybe this will help somewhat..
Put this into your terminal:

```
gsettings set  org.gnome.desktop.wm.preferences button-layout :minimize,maximize,close
```

---

### Post by Frogs Hair on 2012-09-22
Under settings > window manager tweaks > compositor make sure the window decoration is not set to transparent. You would probable remember making this setting and the title bar would disappeared immediately if you had.

---

### Post by Unotforme on 2012-09-24
Thanks for the help, but I decided to backup my data and reinstall. It was a little time consuming, but got the desired result.

If I need to tag this thread solved, let me know.

---

### Post by daslinkard on 2012-09-24
I'm assuming since it is no longer an issue you are seeking....go ahead and mark this as solved.

---

