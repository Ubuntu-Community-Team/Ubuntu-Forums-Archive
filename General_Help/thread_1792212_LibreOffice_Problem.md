---
title: "LibreOffice Problem"
date: 2011-06-27
forum: General Help
---

### Post by tjens09 on 2011-06-27
When I upgraded to Natty, and OpenOffice became LibreOffice, upon opening LibreOffice, the menu headers (File, Edit, etc.) are a series of little "boxes."  Tried uninstalling, and reinstalling, but no avail.  Also tried installing Gnome Office and/or Open Office, (though I know O.O. has been converted to Libre.) but no other Office program shows up in "Applications."  
LibreOffice is still usable, it's just a real PAIN to use...
Any ideas?

---

### Post by dFlyer on 2011-06-27
Don't know if this is your problem but you may have an .openoffice file in your home directory. LibreOffice creates it own .libreoffice file but the two may be confusing the program. If .openoffice is there you might want to try and delete it to see if it helps.

---

### Post by trizrK on 2011-06-27
> **tjens09 said:**
> When I upgraded to Natty, and OpenOffice became LibreOffice, upon opening LibreOffice, the menu headers (File, Edit, etc.) are a series of little "boxes."  Tried uninstalling, and reinstalling, but no avail.  Also tried installing Gnome Office and/or Open Office, (though I know O.O. has been converted to Libre.) but no other Office program shows up in "Applications."  
LibreOffice is still usable, it's just a real PAIN to use...
Any ideas?
you can just run open office through terminal..

---

### Post by SoFl W on 2011-06-27
Did you install the "libreoffice-gnome" package?   (If you are using gnome)  Is that what you mean by "Gnome Office"?

---

### Post by tjens09 on 2011-06-28
> **dFlyer said:**
> Don't know if this is your problem but you may have an .openoffice file in your home directory. LibreOffice creates it own .libreoffice file but the two may be confusing the program. If .openoffice is there you might want to try and delete it to see if it helps.

No, there isn't any .openoffice in Home, thought I'd look in home/.gconf/apps "for fun" but nothing there, either.

---

### Post by tjens09 on 2011-06-28
> **SoFl W said:**
> Did you install the "libreoffice-gnome" package?   (If you are using gnome)  Is that what you mean by "Gnome Office"?

I found it in Ubuntu Software Center.  Description snippet as follows:

[This is a set of applications labeled the "GNOME Office suite". 1:2.30+7ubuntu3 (gnome-office)]

Has this been converted to Libre as well?

---

### Post by markling on 2011-06-30
Why does it seem to difficult to install libre office? Is it only intended for use by the linux elite? Why can't I install it from the Software Centre? (I can't upgrade to 11.04 where Libre comes as standard because 11.04 did not install on my machine). I'm stuck with Open Office but it won't retain its formatting. I think I shall have to see if I can rely on Libre Office. But I downloaded a file with readme instructions that say nothing about Ubuntu.

---

### Post by Hagar Delest on 2011-07-03
For font problem in the menus, just change the font of the system.

Else, try the vanilla version (the same applies to LibO): [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by tjens09 on 2011-07-03
> **Hagar de l'Est said:**
> For font problem in the menus, just change the font of the system.

Else, try the vanilla version (the same applies to LibO): [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

Ah-ha!  That was the problem.  Thanks a lot!

---

