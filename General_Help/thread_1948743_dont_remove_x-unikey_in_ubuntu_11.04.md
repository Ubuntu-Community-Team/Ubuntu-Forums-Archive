---
title: "dont remove x-unikey in ubuntu 11.04"
date: 2012-03-28
forum: General Help
---

### Post by luantruong on 2012-03-28
help me
dont remove x-unikey msg err:
" The package x-unikey needs to be reinstalled, but I can't find an archive for it.
"

i try remove by software center msg err:
"installArchives() failed: dpkg: error processing x-unikey (--remove):
Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.
Errors were encountered while processing:
x-unikey
Error in function: 
"

not access synaptic package maneger, msg err:

"E: The package x-unikey needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
" 

p/s: ubuntu 11.04

---

### Post by luantruong on 2012-03-28
no body can help me?
I need the help of everyone

---

### Post by hansdown on 2012-03-28
Welcome to the forum, luantruong.

Have you tried re-installing with software center?

I will ask the mods to move this thread to a place, that will get you better help.

---

### Post by wojox on 2012-03-28
Ctrl + Alt + T to open a terminal and run:
```
sudo dpkg --remove --force-remove-reinstreq x-unikey
```
Should work.;)

---

### Post by uRock on 2012-03-28
Hello and welcome to the forums. Posting help requests in the Forum Feedback and Help section won't get you any technical help.

Thread moved to General Help.

---

