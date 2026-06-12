---
title: "Help adding a script to shutdown"
date: 2011-01-23
forum: General Help
---

### Post by andrestrevisan on 2011-01-23
Hi. I'm new to linux and ubuntu and i'm having a problem that i don't know how to solve.

I needed the command "sudo shutdown now" to poweroff the pc witch it was not doing, it was going to the recovery menu. What worked to poweroff was "sudo shutdown -P now" i'm using a software that needs to automatically shutdown the pc and the command it uses is shutdown now. So as you can tell that was a problem since it was going to the recovery menu. I contacte the suport of the software and using teamweaver the suport created a script to solve my problem, the script is thhis:

#!/bin/bash
/sbin/shutdown.bin -P now

and saved that as shutdown on the /sbin/ and also created a new file called shutdown.bin witch probably has the original shutdown.

That solved the problem but I had to reinstall the os, so i saved the 2 files (shutdown and shutdown.bin) since i don't now how to do a script etc... reinstalled the os 10.10 and copied the 2 files to the /sbin/ but when i open terminal and type "sudo shutdown now" it doesn't work, obviously there's something more to it than just copying the 2 files. I looked in the /sbin/ directory and did chmod 777 to both files thinking that would solve it, it didn't. Now when i type "sudo shutdown now" this message comes up: 

shutdown.bin: Unable to send message: Connection refused
andre@andre-desktop:~$ 
Broadcast message from andre@andre-desktop
    (/dev/pts/0) at 16:57 ...


Can anyone help me to solve this problem?

Tks

---

### Post by hakermania on 2011-01-23
already asked
[http://ubuntuforums.org/showthread.php?t=844226](http://ubuntuforums.org/showthread.php?t=844226)

---

### Post by realzippy on 2011-01-23
BTW,welcome to the forum!!

*...I'm using a software that needs to automatically shutdown the pc...*

May I ask you to specify?
Maybe existing tools/scripts do the job,eg *gshutdown*..

---

### Post by corncob on 2011-01-23
I would make a launcher.  Right-click the panel and select Add to Panel...  Then the top item - Custom Application Launcher and press Add.  Give it a name and put "sudo shutdown now" in the Command space.  You can change the default icon by clicking on it.
If you want it on your desktop instead of the panel, right-click there and select "Create Launcher...".

---

### Post by andrestrevisan on 2011-01-23
I use a signage software that I program to shutdown at a certain time, and at that time the software lauches the command to shutdown, it uses the command "sudo shutdown now" thats why i have to scpecifically alter that command

---

### Post by dcstar on 2011-01-24
> **andrestrevisan said:**
> I use a signage software that I program to shutdown at a certain time, and at that time the software lauches the command to shutdown, it uses the command "sudo shutdown now" thats why i have to scpecifically alter that command

This will shutdown:

```
sudo init 0
```

---

