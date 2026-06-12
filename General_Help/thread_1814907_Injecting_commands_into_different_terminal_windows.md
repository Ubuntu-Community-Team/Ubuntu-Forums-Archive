---
title: "Injecting commands into different terminal windows"
date: 2011-07-30
forum: General Help
---

### Post by Sebzeppelin on 2011-07-30
Hello all,

I have a terminal window running a game server in Ubuntu 11.04. no problems at all.

I also have a backup script, which simply uses cp to save copies of the level files. this is run as a scheduled task every 20 minutes.

What i'm trying to do, is as part of the backup script issue a command in the game server terminal window (forcing a save of the level) before the cp command takes place.

Two days of googling and i have failed to find a solution, anyone have any ideas?

P.S. one thing i was also trying to figure out is how to identify the game server terminal window, maybe by changing the 'Terminal' text at the top. is this possible?

Thanks for your time,

Sebastian

---

### Post by whitethorn on 2011-07-30
Well I'm guessing there are probably a bunch of ways to get what you want done. I probably wouldn't try to inject a command into the terminal, what about starting a new terminal and have it run the command? 

```
gnome-terminal -e command 
```

As to finding the name of the terminal or setting a name look at the man pages for your terminal.  There's probably an option (--name)

```
man gnome-terminal
```

---

