---
title: "/home/a2z = is my desktop"
date: 2010-01-30
forum: General Help
---

### Post by a2z on 2010-01-30
Hello everybody,

I have a somewhat minor problem. I followed instructions how to set the nvidia xserver via renaming xconfig file (as a precaution) opposed to deleting it. I then saved a new file via nvidia gui.
But somehow I ended up with my /home/a2z as my desktop, and "Desktop.backup" folder on my desktop... Does this make sense?
If anyone would offer a solution to get it switched back around it'd be much appreciated.

Thanks a lot for ubuntu, this community and all who participate.

a2z

---

### Post by blueshiftoverwatch on 2010-01-30
According to [this thread]("http://ubuntuforums.org/showthread.php?t=341607") you can change what folder your desktop points to editing the text file */home/YourUserName/.config/user-dirs.dirs* and changing the *XDG_DESKTOP_DIR="$HOME/"* value to whatever it is you want your desktop to be.

---

### Post by a2z on 2010-01-30
Hi blue, 

Seems more complicated than how I got myself into this predicament.

Thanks for the reply, I'll check into it.

a2z

---

### Post by wojox on 2010-01-30
Hey a2z I've had this problem before. Like blueshiftoverwatch just open .confug/user-dirs.dirs to:

```
XDG_DESKTOP_DIR="$HOME/Desktop"
```

---

### Post by a2z on 2010-02-03
Yes, Desktop back to normal 
Thanks guys!

a2z

---

