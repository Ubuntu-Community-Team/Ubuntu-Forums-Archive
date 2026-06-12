---
title: "where are my applications"
date: 2010-08-24
forum: General Help
---

### Post by jean bonheur on 2010-08-24
Hello,

I'm sorry for the simplicity of the question but I'm new.

I try to find the path where are all the programs, something similar to "program files"  of windows. 

The programs can be accessed by the gui through Application/... but I can't find them neither trough gui folder research nor through the terminal functions I've learned until now. 

(I expect a "terminal" answer )

---

### Post by gavinjb on 2010-08-24
Hi,

there are a couple of places where apps can be installed in Linux, but if you are looking for the path for an app to setup a Desktop Shortcut or something similar then the easiest way is with the following command which will tell you the path for the app

which filename

e.g.

which gedit (returns /usr/bin/gedit on my system)



Gavin,

---

### Post by jean bonheur on 2010-08-25
Thanks a lot.

but isn't there a way to "explore" your files and find your programs? I mean the method you gave me works when you know what programs you have on your computer and the name they have ...

---

### Post by oldos2er on 2010-08-25
Most are in /usr/bin

---

### Post by jean bonheur on 2010-08-25
uh...

I understand there is no such a thing in gnome

thanks anyway ;)

---

### Post by oldos2er on 2010-08-25
> **jean bonheur said:**
> I understand there is no such a thing in gnome


You lost me. Gnome is a desktop environment, it has nothing to do with file system hierarchy.

---

### Post by mendhak on 2010-08-25
No, you should be able to see bin.  Open up any Nautilus window (Places > Home), press Ctrl+L, type in /usr/bin

You'll get a folder with a lot of files in it, though.  I have about 1700.

---

