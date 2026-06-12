---
title: "[SOLVED] Can't Login | Please Help!"
date: 2006-02-17
forum: General Help
---

### Post by xHero on 2006-02-17
Hey,

I did a full install and it asks me for the Breezy Badger Login Info.  What do I put here?

I remember making an account upon full install, but when I go to put in my password, **i cannot type anything** unless I press Enter and go down a line; then it doesn't work.

Please help me out!

---

### Post by kaamos on 2006-02-17
Hello!

Do you have a black (dos-like) window with white text or a graphical enviroment? If it is the first, just type in your password and press enter. You won't get any ***** but the password is inserted.

If you are not getting a graphical enviroment, did you happen to enter "server" into the first installation screen?

---

### Post by xHero on 2006-02-17
Okay so I log in and something comes up like this:

hero@ubuntu~$:

Then what do I do?  Is this the server thing you were talking about?  Can I undo it?  I don't think I chose server.  :confused:

---

### Post by kaamos on 2006-02-17
Ok, first check that you have all the packages installed (if you chose server, this fixes it). Login and type
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```
You have to enter your password and you should have your ubuntu cd in the drive. After these have finished, type
```
startx
```
If it gives errors, post them here.

---

