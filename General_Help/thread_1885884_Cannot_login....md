---
title: "Cannot login..."
date: 2011-11-24
forum: General Help
---

### Post by am_i_registered on 2011-11-24
Hi,

I wanted to remove the encryption from my home directory and i followed this guide:
[http://serverfault.com/questions/160277/ubuntu-how-to-decrypt-home-directory-swap-basically-everything-without-reins](http://serverfault.com/questions/160277/ubuntu-how-to-decrypt-home-directory-swap-basically-everything-without-reins)

However, after rebooting I cannot login to my system. The screen flickers and it returns to the login menu giving no warning...

P.S. I have copied the user folder to an external hdd.

---

### Post by am_i_registered on 2011-11-24
I'm replying to my own thread:

It seems that for some reason the user folder lost ownership.
So I opened a console (Alt+Ctrl+F1) and took ownership of the files by

sudo chwon user /home/user

then, I returned to login menu (Alt+Ctrl+F7) and logged in normally.

---

