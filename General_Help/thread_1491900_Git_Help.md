---
title: "Git Help"
date: 2010-05-24
forum: General Help
---

### Post by seanlano on 2010-05-24
I'm using the Git version of the [game Naev]("http://code.google.com/p/naev") so I can play the latest version and do bug testing, which is currently working just fine. However, according to their website there are other Git branches, each with different versions of the game. I am trying to change from the "master" to ["bigsys" branches]("http://github.com/bobbens/naev/branches/master"), (following [page on Naev wiki]("http://code.google.com/p/naev/wiki/UsingGit")) but when I enter ```
git checkout bigsys
``` I get an error: ```
git checkout bigsys 
error: You have local changes to '.gitignore'; cannot switch branches.

```I presume this is because I used the local git source to compile the binary so I could play the game. 

What can I do to change to the "bigsys" (and/or any other) branch? Will I need to re-clone the naev git repo and then change branch?

---

### Post by NewlyHuman on 2010-05-25
You can undo local changes to a single file with git checkout (e.g. git checkout .gitignore) or completely undo all changes (git reset --hard HEAD).

Be careful with the latter, it will wipe out any local changes without prompting (though you can retrieve lost things from the reflog, if need be).

---

### Post by seanlano on 2010-06-15
Bit late in replying, but this has worked for me. Yay! :p

---

