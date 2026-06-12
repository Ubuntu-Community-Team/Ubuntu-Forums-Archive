---
title: "IE6 on wine for picasa"
date: 2012-06-09
forum: General Help
---

### Post by samwillc on 2012-06-09
Hi everyone,

I have been trying to follow this guide:

[http://www.webupd8.org/2012/01/install-picasa-39-in-linux-and-fix.html](http://www.webupd8.org/2012/01/install-picasa-39-in-linux-and-fix.html)

...and am stuck at this bit (which apparently solves the 64-bit error when installing IE6):

env WINEARCH=win32 WINEPREFIX=~/.wine winetricks
env WINEARCH=win32 WINEPREFIX=~/.wine winetricks ie6
env WINEPREFIX=~/.wine ./picasa39-setup.exe

When do these commands need to be put into the terminal?? After wine install? After picasa install?

Confused by this. Any help would be most appreciated.

Sam.

---

### Post by Frogs Hair on 2012-06-09
Your user info says 12.04 and the tutorial says the following above those commands.> For older Ubuntu versions (like 10.04) which don't have Winetricks available in the repositories or other Linux distributions, install Winetricks using the following commands Winetricks is in the 12.04 repository. Install Picasa is step 2 of the tutorial.

---

### Post by samwillc on 2012-06-09
I got it to install IE6 eventually, then opened picasa, tried to log in and was greeted with a blank white window with no text areas or anything.

To me it's a case of forget about it! I'll use my wifes pc with win7, works on there without faffing around.

It's funny how google are more than happy to use linux but don't support it with making  this product work! I only need it for an assignment on my degree, used it a couple of years ago and wont be needing it in the future after I'm done.

Sam.

---

### Post by samwillc on 2012-06-09
Sorry, this one is unsolved.

Picasa is still in my applications menu even after removing it via wine and then uninstalling wine and wine tricks via software centre.

I want to completely remove picasa, wine, wine tricks and IE6, is there a way to do this via the terminal? I don't need to run any windows programs.

Thanks.

Sam.

**edit** so I removed picasa from the app menu by deleting the hidden .google folder in home. Uninstalled wine through the software centre. What about IE6 though? Is that removed when wine is removed?

---

