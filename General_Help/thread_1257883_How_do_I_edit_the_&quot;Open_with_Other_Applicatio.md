---
title: "How do I edit the &quot;Open with Other Application...&quot; List?"
date: 2009-09-04
forum: General Help
---

### Post by JohnPhys on 2009-09-04
Hey all,

I'm wondering how to edit the list that comes up if you right-click on a file and then click on "Open with Other Application...".  Wine seems to not deal with this list very well, as I have a ton of MS Office entries and "A Wine application" entries in there that are just duplicates and need to be cleaned out.  Any ideas?

Note:  I am *not* talking about the menu that pops up if you right-click and go to the "Open With" menu, I know that one is accessed through the "Properties" when right-clicking on the file.  The one I'm referring to seems to be sort of a "master list" or something.

Thanks!

--John

---

### Post by ackanao on 2009-09-04
This page may help (if I understood you correctly):

[http://ubuntuforums.org/showthread.php?t=1253725]("http://ubuntuforums.org/showthread.php?t=1253725")

---

### Post by mc4man on 2009-09-04
If you are  referring to entries in that list that are typically in lowercase with no icon then browse to 

~/.local/share/applications  (hidden folder in home

You'll find blue diamond userapp.desktops with display names the same as seen in that list.
To check on launch command r. click on properties -> launcher

Deleting them will remove them from the list

(( the 'display' name is not the actual name and entries in the form of userapp-<the displayname>-XXXXXX.desktop will remain in ~/.local/share/applications/mimeapps.list but you can leave them or if further info is needed just ask

---

### Post by JohnPhys on 2009-09-05
Thanks!  That's exactly what I needed!

---

### Post by Andrew_P on 2010-12-16
A related annoyance is that double-clicking on an icon in Nautilus opens the file with the wrong handler.  For example, Ubuntu comes with Firefox as the default browser, but I installed SeaMonkey 2.0 in Lucid Lynx (Ubuntu 10.04.01LTS), and set that as my preferred program in System / Preferred Applications.  However, since I had been opening .html and .htm files with Firefox before I got around to installing SeaMonkey, Nautilus now thinks that I always want to open hypertext documents with Firefox, even though I've selected "Open With ..." and SeaMonkey from the right-click context menu repeatedly since then.  Evidently, GNOME/Nautilus isn't smart enough to figure out my habits.  Here's how to change it:
[LIST]
[*]Browse to [FONT="Courier New"]~/.local/share/applications[/FONT].
[*]Open [FONT="Courier New"]mimeapps.list[/FONT] with gedit or your favorite text editor.
[*]Under the [FONT="Courier New"][Added Associations][/FONT] section, look for the [_[COLOR="Blue"]MIME type[/COLOR]_]("http://en.wikipedia.org/wiki/Internet_media_type") that's causing problems.  (In this example it's [FONT="Courier New"]text/html[/FONT].)
[*]Find the preferred application and move it into the first position after the = sign, making sure that each application is terminated with a semicolon and that the entire line is terminated with a semicolon.
[*]Use this opportunity to delete any unwanted applications, like from the time you inadvertently tried to open a text file with Movie Player.
[*]Save the file and test the change.  When you right-click the icon, the
preferred application should be at the very top of the context menu and the "other" applications should be in the "Open With" submenu.  When you double-click the icon with the left mouse button, the file should be opened with your preferred application.;)
[/LIST]
Here's how it looks in my system:

_WAS_
[FONT="Courier New"]text/html=firefox.desktop;opera-browser.desktop;bluefish.desktop;
gedit.desktop;openoffice.org-writer.desktop;[COLOR="Red"]**seamonkey-mozilla-build.desktop;**[/COLOR][/FONT]

_IS_
[FONT="Courier New"]text/html=[COLOR="Red"]**seamonkey-mozilla-build.desktop;**[/COLOR]firefox.desktop;opera-browser.desktop;
bluefish.desktop;gedit.desktop;openoffice.org-writer.desktop;[/FONT]

N.B. - Be sure you know the nature of the file behind the icon before you double-click it.  You may inadvertently launch a script or something else that does unexpected or nasty things.  Files copied from Microsoft Windows and other operating systems may lack the "executable" permission that Unix-like systems have, and end up being given the executable property by default.

---

### Post by GeorgeStobbart on 2011-02-21
Check the attachment,, if you got the same problem then:
Just right click the Ubuntu Menu Logo, select "edit menu" and remove unused entries under "other",,, also check each menu for any duplicates. ;)

---

