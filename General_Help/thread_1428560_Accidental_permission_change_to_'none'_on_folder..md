---
title: "Accidental permission change to 'none' on folder."
date: 2010-03-12
forum: General Help
---

### Post by Deiyn on 2010-03-12
A rather new user here, was messing with the preferences on a user folder of mine on Karmic, looking for a way to make the folder invisible to users (like the old windows option). Set it to 'none', then closed it, returned to the directory finding the folder with a box with an 'x' on it. 

Went to open it, it says 'access denied'. So I think 'okay, how do I undo that', go back to see if I can restore it back to 'read & write' with no sucess. 

Seached the forums for a solution to this issue, most of solutions revolve around 'gksudo nautilus' which I attempted to open via command-line. Nothing seemed pop open after I entered my password in responce to entering said command-line, probably because I really don't know how to use Nautilus.

If anyone can help I would be very thankful.

---

### Post by J V on 2010-03-12
nautilus is the file manager, gksudo nautilus will pop up a window at /root, you then navigate to the folder and set the perms

---

### Post by asmoore82 on 2010-03-13
I am unable to reproduce this problem, are you really on Xubuntu?
This could be why I can't and might have something to do with no `gksudo nautilus` for you as well.

---

### Post by mcduck on 2010-03-13
> **Deiyn said:**
> A rather new user here, was messing with the preferences on a user folder of mine on Karmic, looking for a way to make the folder invisible to users (like the old windows option). Set it to 'none', then closed it, returned to the directory finding the folder with a box with an 'x' on it. 

Went to open it, it says 'access denied'. So I think 'okay, how do I undo that', go back to see if I can restore it back to 'read & write' with no sucess. 

Seached the forums for a solution to this issue, most of solutions revolve around 'gksudo nautilus' which I attempted to open via command-line. Nothing seemed pop open after I entered my password in responce to entering said command-line, probably because I really don't know how to use Nautilus.

If anyone can help I would be very thankful.

Since you are using Xubuntu you'll need to use "gksudo thunar" to start the file manager XFCE has. Nautilus of course won't work because it's not installed by default in Xubuntu, XFCE's default file manager is Thunar.

---

### Post by Deiyn on 2010-03-13
Thanks, problem solved **@ mcduck.**

---

