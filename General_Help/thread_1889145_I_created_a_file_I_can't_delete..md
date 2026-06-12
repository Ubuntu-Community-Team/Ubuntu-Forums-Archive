---
title: "I created a file I can't delete."
date: 2011-11-30
forum: General Help
---

### Post by utesfan100 on 2011-11-30
I attempted to fuse a file, rather than a directory, and now the file has been corrupted to where I can't delete it.

Here is what I get in the directory the file (badly named .../as3/fusermount) is in

XXX
.../as3$ ls fusermount
ls: cannot access fusermount: Input/output error
.../as3$ rm fusermount
rm: cannot remove 'fusermount': Input/output error
.../as3$ sudo rm fusermount
[sudo] password for mycomputer:
rm: cannot remove 'fusermount': Device or resource busy
 .../as3$ lsof fusermount
lsof: Warning: can't stat() fuse file system .../as3/fusermount
       Output information may be incomplete
lsof: status error on fusermount: Input/output error
lsof 4.81

...

.../as3$ ls -l
ls: cannot access fusermount: Input/output error

...

-????????? ? ?     ?       ?                      ?           fusermount

...

.../as3$
XXX

Any help getting rid of this file would be greatly appreciated.

---

