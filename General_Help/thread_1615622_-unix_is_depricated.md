---
title: "-unix is depricated"
date: 2010-11-07
forum: General Help
---

### Post by tclayson on 2010-11-07
Basically I'm trying to install the meego as per the instructions here: [http://wiki.meego.com/SDK/Docs/1.1/Getting_started_with_the_MeeGo_SDK_for_Linux](http://wiki.meego.com/SDK/Docs/1.1/Getting_started_with_the_MeeGo_SDK_for_Linux)

but when I run $ mad -t <target> qmake I get the error that 

> -unix is depricated

What do I do? If I edit the Makefile can I swap out -unix for something else?


Thanks

---

### Post by ajgreeny on 2010-11-07
When you ran the command ```
$ mad -t <target> qmake
```as you have shown it, did you change the <target> to one of the entries shown in the instructions you linked to?

I hasten to add that I have no idea what meego is, nor what you would use it for, but that will make no difference to the outcome.  The error you got is also not what I would expect if you had not edited the command, which I imagine would be something along the lines of "error: no such file or folder: <target>"

---

### Post by tclayson on 2010-11-07
Well, meego is a mobile SDK for QT Creator.

Yeah target is interchangeable between the two or three targets. I get the same message for all of them.

I guess its probably not an error then, but the outcome of the installation is different to how it is described on the installation wiki.

---

