---
title: "cvs how to"
date: 2010-10-17
forum: General Help
---

### Post by stanley82 on 2010-10-17
Hi,
     I've installed the latest cvs for ubuntu 10/04 and read a couple of how to on the web.  I have environment set for CVSROOT, EDIT and CVSEDIT.  It made me a ~/cvs/CVSROOT and I ran" cvs import mon  Ian_C  START" in my ~/cstuff directory and that has created ~/cvs/mon with my main.c file.  These tutorials do not tell me which main.c file I should edit or how to edit.  Should I edit ~/cvs/mon/main.c or ~/cstuff/main.c, should I just gedit it then do a few cvs commands to generate the diffs or whatever?  Regards Ian.

---

### Post by gmargo on 2010-10-17
All of the directories under the $CVSROOT variable (~/cvs in your case) are your repository directories.  You should never operate on these files directly.

You should edit a checked-out version of the repository.  I'm not sure if your ~/cstuff directory is left in a cvs-usable state, but you can create a new directory and checkout what is in the repostitory, and edit that checked-out copy.

```

cd ~/cstuff
cvs checkout mon
cd mon
.... edit as desired ....

```If you are new to version control, you may prefer newer systems such as subversion (centralized and similar to cvs) or mercurial or git (distributed version control systems).

---

