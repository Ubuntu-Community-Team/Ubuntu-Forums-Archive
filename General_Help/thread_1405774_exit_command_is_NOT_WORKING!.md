---
title: "exit command is NOT WORKING!"
date: 2010-02-13
forum: General Help
---

### Post by squareff255 on 2010-02-13
Hey, so... my exit command won't work. I've attached a jpeg to demonstrate. It's basically just jumping down a line and printing "exit" and then just sitting there... as if it's processing something... I can't press CTRL+D or CTRL+C to get out of it either...
Just wondered if anyone knew.
Thanks. :)

---

### Post by theozzlives on 2010-02-13
Does it echo any other commands, or just exit?

---

### Post by squareff255 on 2010-02-13
JUST exit. It's weird... So I was wondering of there's a file I could modify that could be messed up. I believe there's a file in the /bin directory for each of the commands but I wouldn't know of a way to edit it... or even if that's the right place to look...

---

### Post by john newbuntu on 2010-02-13
Has it been aliased to something?  Type:
alias exit

---

### Post by 3rdalbum on 2010-02-13
> **john newbuntu said:**
> Has it been aliased to something?  Type:
alias exit

I sometimes have this problem when I log into my server over SSH. I don't always have the problem, but it tends to happen when I've been running the connection for a long time.

Typing 'alias exit' into the ssh session gives me "-bash: alias: exit: not found".

This problem doesn't bother me too much as I can just close the window, but I thought I'd give some more information about the OP's (and my) problem anyway.

Also, the problem doesn't happen locally on my desktop or my netbook, or any other machine I've tried. I can't say I've ever had it happen locally on the server either, but then it's usually headless.

---

### Post by squareff255 on 2010-02-13
Nope...
```

bash: alias: exit: not found

```
Thanks tho. It was a good suggestion. I'm so confused!!!

---

### Post by theozzlives on 2010-02-13
When it echos back at you, and you try to close the window, do you get an error that a process is running?

---

### Post by rnerwein on 2010-02-13
> **3rdalbum said:**
> I sometimes have this problem when I log into my server over SSH. I don't always have the problem, but it tends to happen when I've been running the connection for a long time.

Typing 'alias exit' into the ssh session gives me "-bash: alias: exit: not found".

This problem doesn't bother me too much as I can just close the window, but I thought I'd give some more information about the OP's (and my) problem anyway.

Also, the problem doesn't happen locally on my desktop or my netbook, or any other machine I've tried. I can't say I've ever had it happen locally on the server either, but then it's usually headless.

hi
the server is may be running another shell. try "logout" instead of exit.
ciao

---

### Post by squareff255 on 2010-02-13
Well Theozzlives, it does NOT tell me it's running a process or anything when I "X" out of the window. It just shuts off...

and rnerwein, I tried the "logout" command and it says "not a login shell. use: exit"

So weird... Thanks for the suggestions guys. :)

---

### Post by squareff255 on 2010-02-13
Actually, it won't even print anything when I type. I can hit all the keys I want and it will just sit...

---

