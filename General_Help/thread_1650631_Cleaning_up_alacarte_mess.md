---
title: "Cleaning up alacarte mess"
date: 2010-12-21
forum: General Help
---

### Post by cscj01 on 2010-12-21
I customized my Applications Menus over a long period of time.  Then, without warning, application launchers were all over the place rather than where they had been.  So, I tried System->Preferences->Main Menu-> Revert.  Now things are worse than ever.

After doing some digging, I found that an application called alacarte is responsible for maintaing the menu structure and that there are entries in /etc/xdg/menus, ~/.local/share/applications, ~/.local/share/desktop directories, and various other places.

Is there a way I can clean up this mess (mainly get rid of all these files) and start fresh, possibly by reinstalling something?

---

### Post by cscj01 on 2010-12-26
Bump

Surely someone has encountered this type of thing before.

---

### Post by karthick87 on 2010-12-26
```
rm ~/.local/share/desktop-directories/Multimedia.directory
```

---

### Post by cscj01 on 2011-01-01
> **karthick87 said:**
> ```
rm ~/.local/share/desktop-directories/Multimedia.directory
```
Sorry about the delay of my response.  I have been on a little Christmas jaunt.  I do not have a file called Multimedia.directory.  I do have files named Education.directory, alacarte-made.directory, and alacarte-made-1.directory through alacarte-made-8.directory.

Where I have an even bigger mess is in ~/.local/share/applications.  There are many launchers for the same applications such as audacity, brasero, gimp, etc.  Is there any way to determine which launcher in ~/.local/share/applications go with the current menu items?

Perhaps I should just allow this mess to remain.  I have managed to manually re-create my menus as they were using the System>Preferences>Main Menu to move things around.  I probably created a bigger mess in the menus and launchers as I worked on those items, but I did not know of any other way to accomplish what I needed.

What would be nice is to be able to rearrange menus and menu items in a structure you need with a tool that cleaned up all the old stuff.  This alacarte application seems to be an old cumbersome way to manage menus.  Oh well.

---

### Post by djk44883 on 2011-01-19
I have encountered this as well.  About all I can find is a bug report from 2007-05-23 here- [https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/116496](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/116496) then passed here- [https://bugzilla.gnome.org/show_bug.cgi?id=589386](https://bugzilla.gnome.org/show_bug.cgi?id=589386)

And still no remedy.  In alacarte menu editor won't let you change properties.  I manuly edit one of the files only to have it named back to alacarte-made.

---

### Post by djk44883 on 2011-01-19
I have encountered this as well.  About all I can find is a bug report from 2007-05-23 here- [https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/116496](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/116496) then passed here- [https://bugzilla.gnome.org/show_bug.cgi?id=589386](https://bugzilla.gnome.org/show_bug.cgi?id=589386)

And still no remedy.  In alacarte menu editor won't let you change properties.  I manuly edit one of the files only to have it named back to alacarte-made.

---

