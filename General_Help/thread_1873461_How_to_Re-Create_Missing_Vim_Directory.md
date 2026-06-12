---
title: "How to Re-Create Missing Vim Directory?"
date: 2011-11-01
forum: General Help
---

### Post by king0 on 2011-11-01
The /etc/vim directory and the symlinks from /usr/share/vim to it are missing. Does anyone know how to re-create the directory and links?

---

### Post by WasMeHere on 2011-11-01
What about removing and reinstalling vim? I see that I have two packages for vim: vim-tiny and vim-common. I don't know for sure in your version of Ubuntu. Try
```
sudo apt-get purge vim
sudp apt-get install vim
``` and if it complains, try explicitly whatever packages are suggested!

Have fun finding out :-)
Olle

---

