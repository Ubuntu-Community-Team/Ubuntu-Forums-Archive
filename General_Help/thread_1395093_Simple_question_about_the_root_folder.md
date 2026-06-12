---
title: "Simple question about the root folder"
date: 2010-01-31
forum: General Help
---

### Post by Exp HP on 2010-01-31
Forgetting I had used **su** to switch to root (**sudo** didn't seem to be enough for when I was trying to install Java), I had inadvertently created two directories with some files in **/root/** thinking I was in my own home folder.

My question is: [I]Is it important to preserve the structure of the /root folder?
[/I]Put another way: *Should I undo all the changes I made to /root, or is it okay to leave them?*

---

### Post by chewearn on 2010-01-31
If you change what is already there, that could be a problem.  But it's okay if you just create a few more files or directories.

Just like in Windows, you can create a few more folders or files in c:\ but you can't change "c:\program files" to something else.

---

### Post by Exp HP on 2010-01-31
Alright, that's all I needed to know.  I knew I had read somewhere that one of the base level directories contained data used for restoring the system and/or creating new users, but I guess /root is not it.

I deleted the stuff anyways since it was poorly placed (after all, the reason I was trying to put them in my home folder is because I wanted them to be available *without *root access), but I wanted to make sure that just in case I do add files to /root in the future by accident, it's not the end of the world.

---

