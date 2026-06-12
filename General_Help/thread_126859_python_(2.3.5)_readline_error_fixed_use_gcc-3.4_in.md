---
title: "python (2.3.5) readline error fixed: use gcc-3.4 instead"
date: 2006-02-07
forum: General Help
---

### Post by cillian on 2006-02-07
Whoa, this had me stumped for ages!

when doing a custom python compile gcc-4.0 fails to compile readline support with the following error
Modules/readline.c:96: error: static declaration of ‘history_length’ follows non-static declaration

switch to gcc-3.4 instead and it works fine
export CC='gcc-3.4'

(you'll also need to apt-get install libreadline5-dev)

---

