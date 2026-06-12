---
title: "New package: delayedunlink -- recover from accidental deletions"
date: 2006-04-12
forum: General Help
---

### Post by calamari on 2006-04-12
After accidentally deleting some important files this morning, I've made  a tool so that it doesn't happen again.  This package includes a library that replaces the libc unlink call (that deletes files) with code that instead moves the files to subdirectories of **~/.removed/**  .. so no files are lost.  Then, to empty that directory, there is an **empty** command.  

It operates using LD_PRELOAD, and just installing the package is not enough to enable the library.  To enable it, add  the line ```
export LD_PRELOAD=/usr/lib/libdelayedunlink.so.1.0.0
``` to your **.bashrc** file, and reload any open terminals.  

**Please Note:**  While this works great for me, I'm really the only one who has used it, so use at your own risk.  Please let me know if you encounter any problems.

Download: [http://kidsquid.com/dokuwiki/doku.php?id=ubuntu]("http://kidsquid.com/dokuwiki/doku.php?id=ubuntu")

Thanks

---

### Post by hw-tph on 2006-04-12
Neat, I will give it a test run when I have my test box up again.

What license is it released under?


Håkan

---

### Post by calamari on 2006-04-12
[QUOTE=hw-tph]
What license is it released under?
[/QUOTE]

GPL

It was brought to my attention that there are a lot of projects like this already (wish I'd known before yesterday's incident :-|)  One that I found in the Ubuntu repository is libtrash (wow that's a much better name than I came up with). It appears to be built around the same basic mechanism, but is much more mature.  For example, it has different trash cans for each disk.. that is something I didn't think of doing. If I'm not mistaken, it puts all the files in one directory, while mine preserves the original directory structure, so I like that better about mine.  I'm not preserving the original directory permissions, which I should be... guess I found my own first bug.

---

