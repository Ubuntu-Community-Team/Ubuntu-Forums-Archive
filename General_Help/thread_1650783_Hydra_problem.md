---
title: "Hydra problem"
date: 2010-12-22
forum: General Help
---

### Post by Party on 2010-12-22
Hi! I installed hydra with no errors but when i try cracking my password this comes up.

hydra -l root -p passwords.txt 192.168.1.3 ssh2
Error: Compiled without LIBSSH support, module not available!


I tried installing ssh2 with

sudo apt-get install libssh-2-dev

but it says 

Package libssh-2-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libssh-dev

Any help appreciated!

---

