---
title: "Installed with US keyboard, can't switch to UK"
date: 2006-04-24
forum: General Help
---

### Post by greeners on 2006-04-24
I'm a new Ubuntu user, having switched from Fedora after a recommendation from a friend that Ubuntu hardware support is better.  It is! :D 

I found that the DVD distro of 5.10 would crash out if I chose anything other than the defaults.  I'm sure that is an over simplification and the installer may well wrork ok for many users but for me choosing UK language and keyboard options was deadly.  So I allowed the installer to use US language and keyboard settings, figuring I could change it later.

When I open a terminal and try to type @, ", #, \ or | they are all in crazy places as I have a UK keyboard on laptop and clearly a US layout is in use.

I can't switch from the default to a UK keyboard layout. ](*,)   I've tried the System>Preferences>Keyboard layout tool.  I removed the US layout, added the UK layout.  No change. :-k 

Thoughts, suggestions and the answer would be very welcome.

Regards,

---

### Post by dg_w on 2006-04-25
Manage to get in sorted ?

Also try
sudo /etc/X11/xorg.conf  
check this section:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

You can try 
sudo dpkg-reconfigure xserver-xorg

Does the keyboard work correctly in a console (ALT+F1)
If not try:
sudo dpkg-reconfigure console-data

Hope that helps

---

### Post by greeners on 2006-04-30
Yes, editing xorg.conf did the trick.  When I restarted and logged back in an information window appeared to say the X keyboard settings were not the same as the Gnome keyboard settings and would I like to use the X or the Gnome config?  Obviously I chose the X setting option.  

So this points to a problem (bug) in the Gnome keyboard configuration tool ?

Many thanks for your help, much appreciated.

:O)

---

### Post by greeners on 2006-04-30
Yes, editing xorg.conf did the trick.  When I restarted and logged back in an information window appeared to say the X keyboard settings were not the same as the Gnome keyboard settings and would I like to use the X or the Gnome config?  Obviously I chose the X setting option.  

So this points to a problem (bug) in the Gnome keyboard configuration tool ?

Many thanks for your help, much appreciated.

:O)

---

