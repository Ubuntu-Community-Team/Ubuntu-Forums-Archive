---
title: "vi - using arrow keys"
date: 2011-11-21
forum: General Help
---

### Post by Tannor on 2011-11-21
Hi,

I just installed Ubuntu latest version, I have not used it in a few years.

Anytime I try to vi text, and go into insert mode, if i try to hit any of the arrow keys to move around, say up, down, left , or right, instead of moving it creates a new Line with either A,B,C,D.

If I am not in insert mode it works fine.

I am sure it something simple.

I am on laptop, and I have tried turning off and on scroll lock.

Thanks

---

### Post by Foxcow on 2011-11-21
> **Tannor said:**
> Hi,

I just installed Ubuntu latest version, I have not used it in a few years.

Anytime I try to vi text, and go into insert mode, if i try to hit any of the arrow keys to move around, say up, down, left , or right, instead of moving it creates a new Line with either A,B,C,D.

If I am not in insert mode it works fine.

I am sure it something simple.

I am on laptop, and I have tried turning off and on scroll lock.

Thanks

Thats vi for you :D  vim is much nicer and will allow you to do what you want.

```
 sudo apt-get install vim 
```

You can enable color syntax and all sorts of nice stuff much easier.

---

### Post by ratcheer on 2011-11-21
In vi, the j key acts as down arrow, k is up, h is left and l is right.

Tim

---

### Post by Tannor on 2011-11-21
> **ratcheer said:**
> In vi, the j key acts as down arrow, k is up, h is left and l is right.

Tim

Yeah but isn't that in command mode?  not in insert mode?

if i am in insert mode and try those it types the letters out instead of moving?

or maybe I am missing something.

---

### Post by Foxcow on 2011-11-21
> **Tannor said:**
> Yeah but isn't that in command mode?  not in insert mode?

if i am in insert mode and try those it types the letters out instead of moving?

or maybe I am missing something.


vim is vi improved.  Try it and love it.

---

### Post by ikt on 2011-11-21
> **Tannor said:**
> if i am in insert mode and try those it types the letters out instead of moving?

Right, because you're in insert mode.

For me insert mode is for inserting text, and command mode is for moving to the right location and doing commands.

---

### Post by Tannor on 2011-11-21
> **Foxcow said:**
> vim is vi improved.  Try it and love it.

Ok  just installed it and yeah it works great!


Thank you!

---

### Post by lifeboy on 2011-11-21
> **Tannor said:**
> Ok  just installed it and yeah it works great!

You can even install gvim to use for text docs, et al in a GUI and the same keys, searches, etc will work.  And it won't complain about encoding the way gedit does!

---

### Post by Tannor on 2011-11-21
> **lifeboy said:**
> You can even install gvim to use for text docs, et al in a GUI and the same keys, searches, etc will work.  And it won't complain about encoding the way gedit does!


I guess I am just use to redhat, and using the vi it came with.


Thanks!

---

### Post by tankzx on 2011-12-08
> **ikt said:**
> Right, because you're in insert mode.

For me insert mode is for inserting text, and command mode is for moving to the right location and doing commands.

Surely once you're in insert mode you can see a need to move at least left and right!  Also how would you add characters to the end of a line, in command mode you can't move past the last character, you change to insert and characters will be inserted before that last character (if you can't move to the right in inser mode).

Anyway I have the same keyboard problem and I am using VIM, any ideas how to fix that?

Thanks.

---

### Post by Foxcow on 2011-12-08
> **tankzx said:**
> Surely once you're in insert mode you can see a need to move at least left and right!  Also how would you add characters to the end of a line, in command mode you can't move past the last character, you change to insert and characters will be inserted before that last character (if you can't move to the right in inser mode).

Anyway I have the same keyboard problem and I am using VIM, any ideas how to fix that?

Thanks.


While in command mode, you can press 'a' to get into append mode so that you can insert characters after the last.

If you don't have the latest version of VIM, I suggest a quick update:

```
sudo apt-get install vim
```

If you have the latest version, do you still have the problem if you type "vim file" instead of "vi file"  ?

---

