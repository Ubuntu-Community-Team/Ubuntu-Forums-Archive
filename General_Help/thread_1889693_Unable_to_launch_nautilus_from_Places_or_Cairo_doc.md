---
title: "Unable to launch nautilus from Places or Cairo dock"
date: 2011-12-01
forum: General Help
---

### Post by euphgeek on 2011-12-01
I have tried finding an answer to this with no luck.  Any time I try to launch nautilus from the Places menu or from the Cairo dock, this error shows up in .xsession-errors:

Could not parse arguments: Unknown option --browser

I tried launching nautilus from the command line using the option --browser and I get the same error.  Interestingly, the man page for nautilus lists it as a valid option.  Has anyone found any solution for this?  I am using Ubuntu 11.10.

---

### Post by euphgeek on 2011-12-03
I figured it out.  I went through and edited all the nautilus*.desktop  files and removed "--browser" from them.  Now nautilus launches just  fine from both the Places menu and Cairo dock.  But that isn't an ideal  solution for your average user.  If the --browser option isn't going to  be used anymore, nautilus should just ignore it, rather than  refusing to start.

---

### Post by fouadatmeh on 2012-01-19
Where are those nautilus*.desktop files, as I have looked in /usr/share/applications, and I couldn't find any "--browse" in any file..

---

### Post by euphgeek on 2012-01-19
> **fouadatmeh said:**
> Where are those nautilus*.desktop files, as I have looked in /usr/share/applications, and I couldn't find any "--browse" in any file..

I just did a "locate nautilus | grep desktop" to find the files.  If you can't find "--browser" in the .desktop files, then you may not have the same problem.  Check .xsession-errors to make sure that you're getting the same error from my first post that I got.

---

### Post by euphgeek on 2012-01-19
Hi, Rob.  Welcome.

---

