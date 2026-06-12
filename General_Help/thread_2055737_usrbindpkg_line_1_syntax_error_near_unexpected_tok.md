---
title: "/usr/bin/dpkg: line 1: syntax error near unexpected token `newline'"
date: 2012-09-10
forum: General Help
---

### Post by LuisNgo on 2012-09-10
When I tried to run dpkg, I faced this problem:

/usr/bin/dpkg: line 1: syntax error near unexpected token `newline'

What is it and how to fix this?

p.s When I entered folder /usr/bin, I saw that dpkg is a folder not an executable file like dpkg-deb,etc.

---

### Post by spjackson on 2012-09-10
If you are on some recent Ubuntu flavour and /usr/bin/dpkg is a directory, then your system appears to be seriously broken. How did it get in this state? Depending on the answer to that, other things could be broken too.

You cannot install or reinstall packages if dpkg is broken.

The simplest thing might be to boot from installation media and reinstall everything.

---

