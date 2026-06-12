---
title: "Bash scripting"
date: 2011-04-06
forum: General Help
---

### Post by conradin on 2011-04-06
Hi all,
I had a shell script which launches an ssh session, does some stuff and closes. Then moves on the the next ssh session. what I want to do is launch several sessions, or terminal emulation tabs, and work on numerous connections simultaneously.  Does anyone know how how I can write a bash script to open multiple terminal emulations simultaneously? Are there tutorials out there on this sort of thing? I just want to speed up the work I'm doing.

---

### Post by Quintilian on 2011-04-06
the easiest way is to add an ampersand ("&" no quotes) at the end of every command [that you want to run simultaneously, i.e. the ssh sessions]. this spawns a new thread to execute the command. this will execute your scripts more in parallel like it sounds like you want it.

---

### Post by conradin on 2011-04-07
Ah! good idea Quintilian!
But once I launch the processes how might I call them back up?

```

#!/bin/bash
....
ssh -p 4563 xyz@111.222.333.234 & 
ssh -p 4563 xyz@111.222.333.235 & 
ssh -p 4563 xyz@111.222.333.236 & 
ssh -p 4563 xyz@111.222.333.237 & 
(insert generic function to enter passwords or other commands here)


```
How could I pass the expected data to each process?

---

### Post by d3v1150m471c on 2011-04-07
you can use sshpass to pipe passwords and disable the password prompt.
```

sudo apt-get install sshpass
sshpass -pPASSWORD ssh user@hostname

```

you can use `-e' with gnome terminal to push a command to it:
```

gnome-terminal -e <command here>

```

---

### Post by NFblaze on 2011-04-07
You call them up using "jobs".

When you enter the a command with the ampersand (& symbol). The terminal will spit out the line with the job number it was assigned. Such as 

[1] 5323
[2] 7424

Depending on what process you wanted to go back to you would use fg plus the number. So like fg 1 or fg 2 or fg 3, etc...


Learn more about jobs here [http://linuxcommand.org/lts0080.php](http://linuxcommand.org/lts0080.php)

---

