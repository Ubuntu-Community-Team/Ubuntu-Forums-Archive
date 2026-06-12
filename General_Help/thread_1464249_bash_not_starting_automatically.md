---
title: "bash not starting automatically"
date: 2010-04-28
forum: General Help
---

### Post by Dromiidae on 2010-04-28
everytime i open a terminal window, all i see is:

$ _

and i have to type bash everytime to get it running. i found a bandaid fix by having it type bash at the "custom command" profile preference... but i still consider the problem to be unsolved, because i still have to manually type 'bash' whenever i log remotely (putty). it seems like something happened, and now bash is not loaded by the terminal by default like it should.

is there a proper way to fix this? Any help is greatly appreciated.

PS: i already tried 'cp /etc/skel/.bashrc ~./bashrc', and it didn't seem to do anything.

I am using Ubuntu 9.10, fairly fresh install. Had one hard reset since I installed it, which could be when the problem started. Also, I was messing a bit with profiles, switching their ID's and adding/deleting them (not sure if that would be the problem).

---

### Post by spufi on 2010-04-28
Verify whether bash has been correctly set as your users 'shell'.
[SIZE="1"](I don't have an untu box at my disposal right now, so don't know the exact values)
[/SIZE]
Check location of bash executable
```
which bash
```
Check whether this path corresponds to your users home
```
grep -i <your username> /etc/passwd
```
If not, adjust accordingly, but be wary that sometimes the default shell is specified as a symlink to /bin/sh.

---

### Post by Dromiidae on 2010-04-28
Thank you for heading me in the right direction.

I found this command to fix the problem:

[COLOR=#FF0000]chsh -s /path/to/shell {user-name}

[COLOR=Black]The path to my shell (default 9.10 settings) was /bin/bash[/COLOR]
[/COLOR]

---

