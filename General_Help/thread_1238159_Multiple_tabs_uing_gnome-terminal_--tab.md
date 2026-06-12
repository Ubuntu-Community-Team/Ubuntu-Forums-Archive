---
title: "Multiple tabs uing gnome-terminal --tab"
date: 2009-08-12
forum: General Help
---

### Post by AlphaBhat on 2009-08-12
Hail

I've been trying to write a script that launches multiple processes. Was using xterm so far, but the desktop clutter began to get to me

Using gnome-terminal brought a few problems

gnome-terminal --tab -e "cd ..;bash"

Typing this is command line opens a new terminal and closes it immediately. 

Note that if i say only bash in the quotes, or just "gnome-terminal --tab --tab", the terminals stay open. The bash business used to work with xterm but seems to be failing now

Advise.

-AlphaBhat

---

### Post by DaithiF on 2009-08-12
Hi
```
gnome-terminal --tab -e "sh -c \"cd .. && bash\"" --tab -e "sh -c \"cd .. && bash\""
```

note that once you've created a gnome-terminal window there doesn't see to be a way from the command line of opening additional tabs in that window, so whatever tabs you want to create you need to specify at the time of creating the window, ie. with multiple --tab parameters as above.

---

### Post by AlphaBhat on 2009-08-12
Thanks Daithi

Hmm, that works, but still haven't understood the why of it. What's the 'sh -c' for? And why do we need to run bash once more?

---

### Post by DaithiF on 2009-08-12
Hi,
if you try to run gnome-terminal -e "cd ..;bash" directly it will fail -- gnome-terminal expects a program to run, and cd is a shell built-in not a program.  So it will fail to run the command.  Instead we ask gnome-terminal to run a shell, and we pass it a -c parameter for it to execute in that shell.  That command does (1) cd to whatever directory you want, and (2) launches a new bash shell.  The reason (2) is required is that when you pass a -c parameter to the shell, it will execute that command AND EXIT.  So the original shell will close and we're left with a new shell started from the directory you wanted.

cheers
D

---

