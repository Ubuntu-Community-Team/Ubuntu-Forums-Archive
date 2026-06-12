---
title: "Terminal Starts then Closes Immediatly! Need Urgent Help!"
date: 2009-07-08
forum: General Help
---

### Post by wqawasmi on 2009-07-08
Hello, i was messing around with the terminal start up commands and i put this in:
```
gnome-terminal --geometry 50x38; exit
``` So now everytime i turn on terminal it just shuts right back down after its launched. Is there another way to change the start up commands in terminal? Thanx for any help!

---

### Post by kerry_s on 2009-07-08
what? remove the " ; exit " and it won't close.

---

### Post by wqawasmi on 2009-07-08
> **kerry_s said:**
> what? remove the " ; exit " and it won't close.

i know but the way i did it was i edited the profile prefrences through terminal. now i cant do that since it only starts up for 1 second then closes.

---

### Post by unutbu on 2009-07-08
Go to ~/.gconf/apps/gnome-terminal/profiles/
and delete the profile there.

---

### Post by wqawasmi on 2009-07-08
> **unutbu said:**
> Go to ~/.gconf/apps/gnome-terminal/profiles/
and delete the profile there.


did that. still wont work :(

EDIT: I had to restart my computer. THANK YOU!

---

### Post by unutbu on 2009-07-08
[s]
Hm.. Maybe the current gnome-terminal profile is saved in ~/.gconfd/saved_state. Perhaps try logging out, then logging back in. Then try again?[/s]

Oh, good :)

---

