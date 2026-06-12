---
title: "how to open gimp script in ubuntu 8"
date: 2011-01-07
forum: General Help
---

### Post by roquin on 2011-01-07
Hi, guy does some one know how to open gimp files script. i tried this on terminal ; kgsudo nautilus/user/share/gimp/2.0/scripts/ but did not worked. i will appreciate any advice thanks

---

### Post by ajgreeny on 2011-01-07
Was that **kgsudo** a typo?  It should be **gksudo** for GUI applications, but for scripts it is just** sudo**.   You would also need to specify the exact script, not just the folder they are in, and may need to use ```
sudo ./usr/share/gimp/2.0/scripts/scriptfilename
```  Other than that I have no idea.

---

### Post by SteveDee on 2011-01-08
> **roquin said:**
> ...how to open gimp files script....


Gimp scripts files have an ".scm" extension.
The scripts supplied with Gimp are normally located here: /usr/share/gimp/2.0/scripts
...and scripts written by the user should go here: /home/{user}/.gimp-2.6/scripts

You can navigate to these file locations with your file manager (e.g. Nautilus) and open them with your text editor (e.g. gedit). The Gimp supplied scripts will open as read-only, which is probably a good idea!
If you want to open them with write access then run nautilus from a terminal:-
```

gksu nautilus

```
...navigate to the Gimp script location, right click on the script, and then open with gedit.

---

