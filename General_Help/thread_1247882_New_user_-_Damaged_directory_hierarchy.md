---
title: "New user - Damaged directory hierarchy?"
date: 2009-08-23
forum: General Help
---

### Post by CCKrause on 2009-08-23
Three day new to Ubuntu, and it looks like I managed to break something already.

I installed Ubuntu 9.04 AMD 64-bit on a dual Turion processor laptop. I'm using Gnome, default settings, right out of the package. I've only customized colors, wallpaper, panel layouts, panel contents, etc.

I've installed a great deal of software since then - AMP, VirtualBox, Netbeans, etc. etc. - with no problems, although a fair investment in time, so I'd really rather not have to reinstall everything.

This afternoon, I launched Nautilus from Terminal, using Sudo, intending to move a set of unpacked icon directories from [FONT=Courier New]/home/xxxxx[/FONT] to [FONT=Courier New]/user/share/icons[/FONT] (Ubuntu wouldn't move the files without superuser permissions).

I **know** in my haste and flinging the cursor around I grabbed one of the directories in the [FONT=Courier New]usr[/FONT] directory and dropped it inside a different directory; a "chunk" of the listed directories (display in list form) moved *up*.

The customized wallpaper promptly vanished.

Firefox will **not** set an image to a new sceen background.

While the new icon sets are moved into /user/share/icons, and I *can *select a new icon set from the *Appearance Preferences *utility/GUI, the system icons do **not** change and  continues to use the default icon set. Any other changes I make in *Appearance Preferences *also seem to go through (*Appearance Preferences* certainly seems to **think** the changes are made although the desktop disagrees) nothing happens.

Ubuntu and Gnome both seem to be working fine - it is just that I can't **change** anything. While I'm pretty green at all this, it looks to me like it can't find user settings and is just reaching for the defaults set in some other part of the directory heirarchy - could this be right?

Anyone have any idea what it is I did (other than not show due care when running around as a superuser) and how I might fix it?

Thanks

---

