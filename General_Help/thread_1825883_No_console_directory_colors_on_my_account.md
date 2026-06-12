---
title: "No console directory colors on my account"
date: 2011-08-15
forum: General Help
---

### Post by dominiquec on 2011-08-15
Hi, all,

I have a strange problem with the console settings on my command line-only system (10.04, installed via alternate).  For my account, I don't seem to have color for my directories enabled.  It all shows green whatever the file or directory is.

When I log in or sudo as another user, the colors appear fine.  I have tried copying .bashrc from another account, but still no go.  The output of "dircolors -p" from my account and the other account are also the same.

Any suggestions?  Thanks in advance!

---

### Post by dominiquec on 2011-08-17
Found the problem.  It turns out that my account doesn't have the .profile file (why that is, I don't know.)  So therefore my .bashrc wasn't getting read.

---

