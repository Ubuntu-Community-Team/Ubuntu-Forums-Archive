---
title: "After login, system loads root's desktop?"
date: 2011-06-15
forum: General Help
---

### Post by .psd on 2011-06-15
Problem started today:

Upon logging in, the first thing that happens is a prompt for my password to open nautilus. This is because for some reason the system is loading root's desktop instead of mine. While I wait and don't type anything, everything loads normally in the background (with the exception of desktop shortcuts to the files located in /home/anon/desktop). If I decline, I am left with my normal background and a non-functioning desktop (no highlighting, dragging files onto it, or right clicking it) without the files that should be there (all the files in /home/anon/desktop). If I type in the password, or else if after declining if I open gksu nautilus at any time, then the desktop turns into a functioning root's desktop with the default background. All the files in /root/desktop are there, along with the system icons which I have turned off on my desktop. Worth noting that the "Computer" icon on this root's desktop gives an unkonwn filetype error, and the home folder is called "root's Home" and opening it doesn't ask for a password.

tl;dr - The problem seems to be that after logging in, the system is pointed at root's desktop filefolder (/root/desktop) instead of the normal desktop filefolder (/home/anon/desktop). **How do I point it back at the proper desktop?**

---

### Post by .psd on 2011-06-15
Even if you don't know what caused this, doesn't anyone at least know how to point the system back to the proper desktop?

---

