---
title: "Code::Blocks Problem"
date: 2009-09-20
forum: General Help
---

### Post by Hosmion on 2009-09-20
Hey everyone, I was bored today so I decided to make something out of my little bit of knowledge of C++..  So, I saw a thread somewhere that said to use C++ I should use Code::Blocks 8.02..  So I did :D..  But, when I finish all of my coding, save it, and attempt to start debugging, it won't let me..  It is a light gray shade meaning that I cannot click on it..  What should I do?

:guitar:ROCK ON UBUNTU:guitar:

**EDIT::**

Also, I must have pressed something, but this image popped up (see attachment)

How do I remove it?

---

### Post by ibuclaw on 2009-09-20
Install build-essential and gdb?
```
sudo apt-get install build-essential gdb
```
Then set the debugger application to **/usr/bin/gdb** in Codeblocks.

edit:
Hmm, I didn't see that image first time.

Can you move it around by holding down **Alt** and clicking/dragging it?


Regards
Iain

---

### Post by Hosmion on 2009-09-20
> **tinivole said:**
> Install build-essential and gdb?
```
sudo apt-get install build-essential gdb
```Then set the debugger application to **/usr/bin/gdb** in Codeblocks.

edit:
Hmm, I didn't see that image first time.

Can you move it around by holding down **Alt** and clicking/dragging it?


Regards
Iain
No, I cannot move it..  I even uninstalled and reinstalled it without success..

I did the firstthing though, thanks!
Well, I downloaded it anyway..

---

### Post by Hosmion on 2009-09-20
I fixed the image finally..  I set the bar at the top to auto-hide and I could see how to move it and stuff..  Finally :)

EDIT::

How do I make it so I can make the default compiler what you told me to install?  What do I choose to open and choose what I want the default to be?

---

### Post by ibuclaw on 2009-09-22
> **Hosmion said:**
> I fixed the image finally..  I set the bar at the top to auto-hide and I could see how to move it and stuff..  Finally :)

EDIT::

How do I make it so I can make the default compiler what you told me to install?  What do I choose to open and choose what I want the default to be?

gdb isn't a compiler ... it's a debugger.

---

