---
title: "File browser wont open?"
date: 2009-12-07
forum: General Help
---

### Post by Phospholipid on 2009-12-07
Hi all,

I just installed 9.10, then went about installing UNR, i then tried to open my /Desktop from the UNR shortcut which comes up with the opening "message" in the middle of the screen and then goes back to normal without opening the file browser. i tried the other shortcuts to no avail and tried the Places > Desktop again with no result. I checked using the terminal to find that the directories are present and correct so there shouldn't be a problem.

I am wondering if I do not have a file browser? or if it is broken and needs reinstalling? if so what is it called?

thanks to anyone who can help!

---

### Post by Bradj47 on 2009-12-07
Try typing **nautilus** into the Terminal.

---

### Post by Phospholipid on 2009-12-08
Hi there,

thanks for your reply,

I typed nautilus into the terminal and got out this

> (nautilus:1925): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Bus error

and I am not sure what this means except that nautilus did not run due to an error getting a variable.

what shall I try next?

---

### Post by audiomick on 2009-12-08
Can't help much but:
nautilus is the file browser. Typing "nautilus" in the terminal should start the file browser. As you can see from the message, it generates some kind of bus error, and seems to fail to initialize some preferences.

It looks like the nautilus installation might be broken. You should wait for further replies. Maybe someone can tell you how to fix it.

---

