---
title: "awkward disk capacity problem"
date: 2011-10-17
forum: General Help
---

### Post by bbinb on 2011-10-17
Hi everyone

I had a really awkward problem today.. I have been using ubuntu 11.04 LTS for nearly 2 months without a problem.. Today I have tried to copy a file from a flash disc and I got an error saying:
"not enough space".. However, I know that I still have at least 90 Gbyte free space. When I opened the home folder I see at the bottom of the page 183.6 Mbyte free space.!? home folder seemed to be full but it actually is not! Disk utility says that the part of the hard disk which ubuntu is loaded is healthy.. 

If anyone experience such kind of situation pls give some advice...

---

### Post by JKyleOKC on 2011-10-17
Check your "trash" folder. The default, when you "delete" a file or directory, is actually to just copy it over to the trash folder so that you can bring it back if you change your mind. However, it's still taking up space.

If the trash folder is empty, the next place to look is in /var/log to see if you have one or more "runaway" log files that are chewing up all of your space. If you do, you can simply delete the offender using "sudo" but be sure to empty the trash for the super user afterward.

Incidentally, 11.04 is not a LTS release. LTS (Long Term Support) versions appear only at two-year intervals, and the current one is 10.04.3.

---

