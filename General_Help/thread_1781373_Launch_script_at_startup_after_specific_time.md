---
title: "Launch script at startup after specific time"
date: 2011-06-13
forum: General Help
---

### Post by Marcelo Ruiz on 2011-06-13
Hi All!

I have a problem that I don't know how to solve and maybe some of you can give me an idea!
I'm running Ubuntu 10.10 in a computer with a 7200rpm HD, 8Gb Ram, and a Core i7, and the time it takes to load the desktop is insane. There are threads that mention the problem of gnome looking for nonexistent floppy drives and to solve the problem by disabling that in the BIOS (option I don't have).
Anyway, besides that problem, by running at startup a gnome-terminal with the iotop command, I noticed that two processes have a huge i/o load on the system: google desktop and ubuntu one.
I would like those programs to run as part of the startup process, but be launched after several seconds (to allow the rest of the programs to load). Is there any way I can achieve this? I think there should be a way modifying the commands under startup application, but I cannot find anything that works.
Thanks!

---

### Post by doas777 on 2011-06-13
usually what I do, is move the command to a script and use a sleep statement to pause teh thread for x seconds before execution
```

#!/bin/bash
sleep 20
<command>

```

save the above to a file (with your own command and sleep time)
make it executable (sudo chmod u+x <pathtofile>)
and then in your Startup Applications, add a reference to the script instead of the command itself.

---

### Post by Marcelo Ruiz on 2011-06-13
Thanks! That worked!

---

