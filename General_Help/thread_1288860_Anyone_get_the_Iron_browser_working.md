---
title: "Anyone get the Iron browser working?"
date: 2009-10-11
forum: General Help
---

### Post by monkeyKata on 2009-10-11
Hello.  I've downloaded the latest tar.gz from here:
[http://www.srware.net/forum/viewtopic.php?f=18&t=561](http://www.srware.net/forum/viewtopic.php?f=18&t=561)

and extracted it to my home folder but cannot get it to run.  I double click 'iron' and nothing happens, likewise if I try through the terminal as "iron --enable-plugins"

I couldn't find a ppa and I don't believe there's a deb file.  Just wanted to know if anyone had gotten this installed and working, and I wonder, too, if extracted the tar.gz file is all you need to do.  Perhaps some dependencies are needed.

---

### Post by monkeyKata on 2009-10-12
bump

Couldn't find any other postings on this.  Also don't think it needs to be compiled as it doesn't have any configure file and running "make" in the terminal said there was nothing to make.

---

### Post by monkeyKata on 2009-10-12
also...

Trying to run it in the terminal gives a "Segmentation fault."  Is this the right way to phrase the command to run/execute the application from within the folder

./iron

?

It's possible it should work fine and I just don't know what I'm doing.  I don't have any other apps I haven't downloaded either from the official repositories, a ppa, or from a deb file found online.  Do tar.gz files (that do not seem to have the source code and not compilable) just need to be extracted somewhere, then their executable ran?

Stubbornly hoping someone on the forums tonight (or today) has gotten this web browser working and can offer some light or see any error I'm making.

Oh, and if you don't know what Iron is, it's Google's Chrome browser but without several features that are privacy concerns for many.

[http://www.srware.net/en/software_srware_iron.php](http://www.srware.net/en/software_srware_iron.php)

---

### Post by dagodemon42 on 2009-10-13
You might try to change to the proper directory in the terminal, then execute the ./iron command. Also make sure the iron-linux file is executable. Find the iron-linux folder, then the iron-linux icon, right click and select the permissions tab and make sure execute box is checked.

---

### Post by monkeyKata on 2009-10-13
Thanks for the help.

I looked in the permissions and the execute box is checked.  I'll keep at it...

---

### Post by Toost Inc. on 2010-03-23
Having the same problem with version 4.0275 Beta. Only when I try to run it in the Terminal it won´t even give me an error.

---

### Post by patchwork on 2010-03-23
Have you made it executable?

```
sudo chmod +x /path/to/iron
./iron
```PS.  It's pretty slick if you haven't used it before...

---

