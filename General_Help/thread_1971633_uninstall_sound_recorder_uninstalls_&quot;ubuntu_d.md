---
title: "uninstall sound recorder uninstalls &quot;ubuntu desktop system&quot;"
date: 2012-05-02
forum: General Help
---

### Post by akidd on 2012-05-02
and after doing so after a restart you get nothing but  a black screen?  Huh?

I assume this is a bug as the dependencies can't be everything and even if they are they should be amended to not remove the desktop because I don't want Sound Recorder

---

### Post by Dennis N on 2012-05-02
ubuntu-desktop is what is called a 'metapackage'. It is a special package that is basically a list of dependencies or recommended packages to install. However, when you remove ubuntu-desktop metapackage, none of those packages is removed with it. You are just removing the list (metapackage) without removing any of the items on the list that it installed. 

Maybe this will help:
 
[http://askubuntu.com/questions/66257/what-is-the-difference-between-a-meta-package-and-a-package](http://askubuntu.com/questions/66257/what-is-the-difference-between-a-meta-package-and-a-package)

---

### Post by akidd on 2012-05-03
Thanks Dennis.  "Too much Ubuntu"!  :)  Thanks for the links.  I've read and think I understand.

I am removing the stuff I don't want/use and I am curious why the metapackage is removed?  Does this mean all the dependencies or recommended packages are also removed?  Otherwise why remove the list?

I did remove the sound recorder and the wacom tablet dependencies during a single session.  Afterward the system would no longer boot.  Doesn't this sound like a bug?

Removing "Wacom model feature query library"

libwacom2 - Removes 10 packages that include: 

- gnome control center (really I just wanted the icon gone from system settings) 
- gnome session 
- ubuntu desktop 
- indicator session 
... 

Is...

---

