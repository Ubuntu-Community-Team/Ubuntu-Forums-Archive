---
title: "Adding Multiple Commands to Launcher (cd &amp; mono)"
date: 2011-02-07
forum: General Help
---

### Post by TurtleKing on 2011-02-07
Okay, so I am trying to make a launcher under application/Games menu for OpenBVE. In this launcher I need it to run 2 commands in the terminal:
```
cd /home/username/OpenBVE
```
and
```
mono OpenBve.exe
```

They are other options of installing the game, but I am doing the manual install with a launcher (before the get it from Software Center Spam begins).

This is currently the command I had setup:
```
cd /home/myusername/OpenBVE && mono OpenBve.exe
```

However, the terminal respond with a window:
```
There was an error creating the child process for this terminal
Failed to execute child process "cd" (No such file or directory)
```

I need the terminal to switch to the "OpenBVE" folder, and then mono the "OpenBve.exe".

Any help how to get the launcher to do those 2 commands in order please?

---

### Post by ajgreeny on 2011-02-07
Can you not just use the full pathway to the OpenBve.exe file with a single command?```
mono /home/user/OpenBve.exe
```

It seems to make sense, but then I know nothing about mono or the way it works.

---

### Post by TurtleKing on 2011-02-07
Tried it and it and launcher doesn't respond. :(

---

### Post by sisco311 on 2011-02-07
Run the commands in a shell:
```
sh -c "cd /path/to/dir && mono whatever.exe"
```

---

### Post by TurtleKing on 2011-02-08
> **sisco311 said:**
> Run the commands in a shell:
```
sh -c "cd /path/to/dir && mono whatever.exe"
```
Awesome, thanks for the help. Man you guys can fix anything. Now how do I fix my super scanner on my teleportation machine. :-\"(joking)

---

