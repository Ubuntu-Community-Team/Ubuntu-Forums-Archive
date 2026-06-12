---
title: "cuting/pasting large files"
date: 2011-02-28
forum: General Help
---

### Post by ELD on 2011-02-28
Okay basically i have a media drive full of crap i am trying to move to another hard drive.
 
Ubuntu gives me an error message stating the file is too big to move, there must be a way to move large files? Im talking files like 7GB big.
 
It can't just be impossible or i fail to see how people editing videos could use Ubuntu? (Not bashing, just really need to know!)

---

### Post by wt8008 on 2011-02-28
You can try using the mv command in the terminal. 
Try
```
mv -v SOURCE DEST
```
where SOURCE is the source filename and path and DEST is the destination filename and path. See [http://manpages.ubuntu.com/manpages/maverick/man1/mv.1.html](http://manpages.ubuntu.com/manpages/maverick/man1/mv.1.html) for more information.

If you are new to the command line, you may want to practice with cp, the copy command instead. See [http://manpages.ubuntu.com/manpages/maverick/man1/cp.1.html](http://manpages.ubuntu.com/manpages/maverick/man1/cp.1.html)

---

