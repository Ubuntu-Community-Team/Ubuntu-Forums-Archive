---
title: "Keep Workspace Setup"
date: 2006-06-15
forum: General Help
---

### Post by leetcharmer on 2006-06-15
I've found a perfect combination of windows that help me work effectively and I've placed them on Workspace 4 for when it's time to do work; is there a way to tell Ubuntu to *remember* those applications and when I hit a hotkey or something, it would open them on workspace 4?

---

### Post by Lunar_Lamp on 2006-06-15
I think devilspie *may* be able to do this - but I haven't used it really myself.  You may want to check it out.

---

### Post by frodon on 2006-06-15
I would create a script which launch all these apps and create a shorcut to lauch the script, and for the window size and position i would handle them with devilspie.

---

### Post by leetcharmer on 2006-06-15
devilspie doesn't come with a worthy man page, can you show me an example of a command to use?  I want vmware to take up the right half of workspace 4, with calculator to be top left space and OO.o Writer on bottom left space -- all workspace 4.

---

### Post by frodon on 2006-06-15
This link will provide you all the needed informations to start with devilspie : [http://wiki.foosel.net/linux/devilspie](http://wiki.foosel.net/linux/devilspie)

You may need to create the .devilspie directory where you put the .ds files.
Ps: the link i gave you is for the latest version of devilspie which is on the dapper repositories.

This is a useful command which will return you the name of the window : ```
xprop | egrep "(WM_WINDOW_ROLE)|(WM_CLASS)"
```Click on a window you want to know more about, and you will get an output like: > WM_WINDOW_ROLE(STRING) = "conversation" 
WM_CLASS(STRING) = "gaim", "Gaim"

You're ready to start now ;)

---

