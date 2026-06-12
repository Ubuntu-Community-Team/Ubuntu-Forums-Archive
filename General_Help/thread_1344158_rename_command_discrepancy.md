---
title: "rename command discrepancy"
date: 2009-12-02
forum: General Help
---

### Post by blur xc on 2009-12-02
Well, as I study the command line, I finally got to the rename command.  It's a lot more powerful that what I remember from back in my dos days...  So, I google around, and find tutorials that show the syntax as "rename foo bar *.txt".  I tried that, and got an error.  I was confused.  I read the man page, and was even more confused.  I don't know what a perl expression is (at least I didn't).  So, I google some more and come accross this syntax "rename 's/foo/bar/' *.txt".  That worked.  

So, it had me wondering- when and where does that first (less complicated) syntax work?

sources- 
[http://kangry.com/topics/viewcomment.php?index=538](http://kangry.com/topics/viewcomment.php?index=538)
[http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal](http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal)

Thanks,
BM

---

### Post by kaibob on 2009-12-02
There are different versions of the rename command. The one included in Ubuntu is is actually a perl script called prename. The other rename command is included in Ubuntu as rename.ul. Look at the man pages for rename and for rename.ul to see the differences. 

The following post has some excellent examples of the perl-based rename command:

[http://ubuntuforums.org/showthread.php?p=5210531](http://ubuntuforums.org/showthread.php?p=5210531)

---

### Post by blur xc on 2009-12-03
Sweet- tried it out.   Thanks for the info...

BM

---

### Post by jegerjensen on 2009-12-03
Amazing!  I didn't know about the rename command:D

---

### Post by blur xc on 2009-12-03
> **jegerjensen said:**
> Amazing!  I didn't know about the rename command:D

It's an amazingly powerful command.  And if you haven't tried it yet, give the find command a whirl.  That's some seriously useful shiznit that afaik, can't be duplicated in the gui.

BM

---

