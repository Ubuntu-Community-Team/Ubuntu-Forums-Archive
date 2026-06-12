---
title: "need permission to save in Wine ?"
date: 2011-01-27
forum: General Help
---

### Post by garyed on 2011-01-27
I'm having a problem saving a file running this program in Wine.
If I choose save as & put it in my home folder it works but it won't save in the program folder I'm using it in. I get this permission problem. I own the directory & gave full access to the files for everyone with chmod 777

I'll try to post a screenshot.
Any help appreciated

---

### Post by Mark Phelps on 2011-01-27
It may not be a permission problem at all -- it may simply be the way that Wine's implementation works.

MS Windows, in recent versions, actively tries to prevent you from saving anything in Program Files, and instead, tried to force you to save files in directories that you "own".

It may be that, in being faithful to the Windows way of doing things, Wine may simply be doing it the "MS way".

---

### Post by garyed on 2011-01-27
> **Mark Phelps said:**
> It may not be a permission problem at all -- it may simply be the way that Wine's implementation works.

MS Windows, in recent versions, actively tries to prevent you from saving anything in Program Files, and instead, tried to force you to save files in directories that you "own".

It may be that, in being faithful to the Windows way of doing things, Wine may simply be doing it the "MS way".

I think you're right because I can save the files in other directories from that program that have the same permissions & there's no way that I can find to tell Wine that I'm the admin. I haven't tried running Wine as root but I don't like the thought of messing with anything associated with Windows as root.

---

