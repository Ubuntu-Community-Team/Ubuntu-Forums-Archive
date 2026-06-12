---
title: "Trouble with Ubuntu Software Centre"
date: 2010-09-14
forum: General Help
---

### Post by lokino on 2010-09-14
I've been trying to find Nethack-console, I originally couldn't find it in Ubuntu Software Centre so I found a front end download and tried to install it using Synaptic. It wouldn't work apparently because it was 32-bit instead of 64-bit. 

I gave up and was playing Nethack-X11 till I finally found it by chance in USC. Apparently it isn't in the games section, because I found it by searching 'Nethack' straight away under Get Software. I got rid of Nethack-X11 and installed Nethack-Console. Now I can't find it again, it's not under applications and isn't listed when I try using Run Application. 

I checked and it says I have nethack-common & nethack-console installed. I'm out of ideas, can anyone help?

Also I'm sorry if this is in the wrong thread.

---

### Post by lokino on 2010-09-14
Nevermind, I found the folder (it was in /usr/games) and it seems to only respond when I run it in the terminal. Unfortunately when I do I get
```

NetHack, Copyright 1985-2003
         By Stichting Mathematisch Centrum and M. Stephenson.
         See license for details.
Waiting for access to /var/games/nethack/perm.  (9 retries left).
Waiting for access to /var/games/nethack/perm.  (8 retries left).
Waiting for access to /var/games/nethack/perm.  (7 retries left).
Waiting for access to /var/games/nethack/perm.  (6 retries left).
Waiting for access to /var/games/nethack/perm.  (5 retries left).
Waiting for access to /var/games/nethack/perm.  (4 retries left).
Waiting for access to /var/games/nethack/perm.  (3 retries left).
Waiting for access to /var/games/nethack/perm.  (2 retries left).
Waiting for access to /var/games/nethack/perm.  (1 retries left).
Waiting for access to /var/games/nethack/perm.  (0 retries left).
I give up.  Sorry.
Perhaps there is an old /var/games/nethack/perm_lock around?

Hit space to continue: 







```Then it closes after I hit space. So now i have a new problem.

---

### Post by lokino on 2010-09-14
Found a fix here :-|
[http://ubuntuforums.org/showthread.php?p=9846380#post9846380](http://ubuntuforums.org/showthread.php?p=9846380#post9846380)
sorry for the wasted thread. #-o

---

