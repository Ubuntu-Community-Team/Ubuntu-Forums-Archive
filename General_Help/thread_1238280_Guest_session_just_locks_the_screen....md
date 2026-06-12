---
title: "Guest session just locks the screen..."
date: 2009-08-12
forum: General Help
---

### Post by Upkeep on 2009-08-12
Hi there,
 
I'm running 8.10 on an HP2133 Mini-Note.  I was having a look at the "guest session" option, but all that seems to happen when I select it, is that it locks my screen.  By "lock", I mean that I need to enter my password again to start my session rather than it locks up.
 
What am I doing wrong guys?
 
Upkeep

[Update]  For anyone who runs into the same problem, here's the answer.  The chances are, your guest session doesn't work because you've created a proper user account that is also called "guest".  Even if you remove the user account for "guest", the folders still exist for it and you need to get rid of them.  I did this the following way:

Open a terminal and navigate to /home$

To get rid of the files and folders for "guest" enter: sudo rm -rf guest

Bingo - job done and the guest session function will work again

---

