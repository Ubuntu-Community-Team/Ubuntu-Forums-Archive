---
title: "Man search path"
date: 2009-10-04
forum: General Help
---

### Post by asian_al on 2009-10-04
What file would I edit in order to change the man search path permanently?  I was thinking whereis man ?

---

### Post by falconindy on 2009-10-04
whereis only shows you where to find whatever your search parameter is. You cannot "edit" the result. The `manpath` command is probably what you're looking for.

---

### Post by ermeyers on 2009-10-04
man manpath
/etc/manpath.config

---

### Post by asian_al on 2009-10-04
what about which man? What if I wanted to find the source code of a command? Like the cd command? would that be the which cd command?

---

### Post by falconindy on 2009-10-04
I don't think `which` does what you think it does. If you want to see source code, you need download it from the appropriate source. In this case, low level commands like `cd` or `ls` are going to be part of the shell that you're using (e.g. bash, ksh, csh, dash, etc). Bash source code can be obtained from gnu.org.

---

