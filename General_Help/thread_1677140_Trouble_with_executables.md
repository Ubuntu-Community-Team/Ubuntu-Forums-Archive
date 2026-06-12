---
title: "Trouble with executables"
date: 2011-01-28
forum: General Help
---

### Post by Skeet Monroe on 2011-01-28
Hello.  I'm new here, so if I posted in the wrong place, please let me know where to post.  I have a copy of AutoCAD, and tried installing it, but the setup.exe file is apparently unexecutable in ubuntu.  I tried changing it to executable, but the disc is closed and is in read-only.  Does this mean that I can only use CAD on my windows laptop?  Or is there some way around this?

Thanks,

Skeet

---

### Post by Cuddles McKitten on 2011-01-28
In general, it's best to run Windows programs in Windows.  However, there is something called "Wine" which can allow you to run some Windows programs reasonably well (and AutoCAD may very well be in this category).

Anyhow, your problem is that all executables (or binaries) from outside sources are, by default, unexecutable as a security precaution.  Assuming you use GNOME (the default desktop manager for Ubuntu), right click on this file, go to "properties," click on the "permissions" tab, and check the "allow execution of file as a program" box.  Then press OK.  Now if you double click on the file, Wine should automatically run it for you.  If not, try right clicking on the file again and choose "open with Wine Windows program loader."

---

### Post by Skeet Monroe on 2011-01-28
That was what I tried first.  When I tried clicking the button to make it executable, I get a message that says the disc is read-only, so I can't change it.  I can open the read me and everything, just not the setup.

---

### Post by Mark Phelps on 2011-01-28
The link below is to the WinHQ app compatibility page for AutoCAD:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=86]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=86")

As you can see, quite a few are rated Garbage -- meaning, they will not run no matter what you do.

IF your version is one of those, you are out of luck.

---

### Post by Skeet Monroe on 2011-01-28
Well it looks like I'm lucky...at least sort of.  My cad is 2004, and it is rated gold.  That means If I can get the thing to execute, then it should work, right?  I'm still not sure how to get it to work, though.

---

