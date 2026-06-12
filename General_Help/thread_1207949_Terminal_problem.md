---
title: "Terminal problem"
date: 2009-07-08
forum: General Help
---

### Post by knopper67 on 2009-07-08
I just tried out Gnome shell, It compiled just fine, but something got messed up in the process.

From now on, every time I start the terminal it cd's into the source directory (~/gnome-shell/source/gnome-shell/src). 

Before all of this, it just landed in my home directory as usual.

Anyone have a clue how to fix this?

---

### Post by Jebtrix on 2009-07-08
Try:

```
gnome-terminal --working-directory=/whatever/directory/you/want 
```

Or in the source/scripts just look for the clue --working-directory=

---

### Post by knopper67 on 2009-07-08
I don't want to have to use a workaround..

Before I installed gnome-shell everything was fine and it would land in my home directory each time. Now it keeps landing inside the gnome-shell source directory where I compiled it.

Also, the $PWD environment variable keeps getting reset everytime I close the terminal. That's what's causing the problem, but I have no idea how to fix it.

---

### Post by wojox on 2009-07-08
What Jebtrix told you to do didn't work?

That's what the man command suggests.

---

### Post by Jebtrix on 2009-07-08
Problem may be in /etc/bash.bashrc or ~/.bashrc

---

### Post by knopper67 on 2009-07-08
The _workaround_ did work, yes.

But why is it doing this in the first place? I'd rather fix the actual problem (If I knew how). It keeps changing the working directory of the terminal to "~/gnome-shell/source/gnome-shell/src" even though it doesn't exist anymore.

---

### Post by knopper67 on 2009-07-08
I deleted my .bashrc file to see if that would fix it.

It Didn't, though.

---

### Post by Jebtrix on 2009-07-08
I guess I would check anything in the 'bash' chain, like:

/etc/profile
/etc/bash.bashrc

Or do a text search in the source you compiled looking for any references/changes to these files...:???:

Or just take a swing at it with a filesystem text search everything for "gnome-shell/source/gnome-shell/src"

---

### Post by knopper67 on 2009-07-08
Thanks for the help. But I think the problem solved itself. Id did a quick reboot and the problem seems to have all of a sudden vanished.

Thanks a lot for the help though, I appreciate it. :)

---

### Post by Jebtrix on 2009-07-08
Good to hear that. Honestly if some package needs to be compiled, I highly recommend doing it in a virtualbox so you dont bork your system. Usually if I'm really motivated, I use remastersys to make a 'clone' of my system with settings, and then mount that iso to create a virtualbox clone.

---

### Post by knopper67 on 2009-07-09
Thanks for the tips. I'll note those down for the future. Thanks again.

---

