---
title: "Won't allow me to transfer a file to a directory."
date: 2009-09-10
forum: General Help
---

### Post by Lyerae on 2009-09-10
I'm trying to transfer a language file for gedit to "/usr/share/gtksourceview-2.0/language-specs", and it keeps denying it... How can I make it so I can transfer the file?

Thanks for any help.

---

### Post by yabbadabbadont on 2009-09-10
You'll have to either use sudo in a terminal window with the cp or mv commands, or launch nautilus using gksudo (or gksu, I forget which).

Edit: It looks like you would use gksu to launch nautilus.

---

### Post by Lyerae on 2009-09-10
How do I do that?

---

### Post by yabbadabbadont on 2009-09-10
In Gnome, hit Alt-F2 to open the run dialog.  Then enter ```
gksu nautilus --no-desktop
```
It should prompt you for your password.  Then you should be able to copy or move the file.

---

### Post by Lyerae on 2009-09-10
Didn't work...

---

### Post by wojox on 2009-09-10
Open the terminal:

```
gksudo nautilus
```

---

### Post by ithinkitschad on 2009-09-10
> **Lyerae said:**
> I'm trying to transfer a language file for gedit to "/usr/share/gtksourceview-2.0/language-specs", and it keeps denying it... How can I make it so I can transfer the file?

Thanks for any help.

you can..

sudo chown username:username /path/to/folder

---

### Post by yabbadabbadont on 2009-09-10
> **ithinkitschad said:**
> you can..

sudo chown username:username /path/to/folder

You *really* don't want to do that to a system directory...

To the OP, sorry for the late reply, gksudo nautilus was what I was going to tell you to try next, but wojox beat me to it.  :D

---

### Post by ithinkitschad on 2009-09-10
> **yabbadabbadont said:**
> You *really* don't want to do that to a system directory...

To the OP, sorry for the late reply, gksudo nautilus was what I was going to tell you to try next, but wojox beat me to it.  :D

Yeah, very true.

---

### Post by Lyerae on 2009-09-10
Aha! It works! Thanks!

---

