---
title: "&quot;at&quot; command: only parts of my script are executed"
date: 2012-02-08
forum: General Help
---

### Post by Thorsen V on 2012-02-08
I'm trying to put together a simple reminder system using the "at" command.

Basically I'd like to be able to launch a gui application from a script triggered by "at", at the specified time, eg:
[INDENT]$ at 22:00
warning: commands will be executed using /bin/sh
at> /home/thorsen/myscript.sh        
at> <EOT>
job 18 at Thu Feb  9 22:00:00 2012
[/INDENT]myscript.sh might look something like this:
[INDENT]#!/bin/sh
echo running ... > /home/thorsen/myscript.log
gedit /home/thorsen/22:00.reminder.txt &
echo ... done. >> /home/thorsen/myscript.log
[/INDENT]Basically the log files has the messages but gedit doesn't launch.
I've messed about with this (including putting a sleep command at the end of the script in case it was something to do with the shell closing before gedit got to paint its client window) but no luck.

I'd appreciate any help.

Thanks


I'm using ubuntu 10.04

---

### Post by Khayyam on 2012-02-08
Thorson ...

My guess (sorry its late) is that it doesn't know what DISPLAY to use and so gedit doesn't launch.

```
#!/bin/bash
export DISPLAY=:0
echo "."
gedit &
echo "."
```Again, its late and so take this as a tardy reply ..

HTH ..

---

### Post by Thorsen V on 2012-02-08
That's done the trick ... Thank you Khayyam :D

---

### Post by Khayyam on 2012-02-09
> **Thorsen V said:**
> That's done the trick ... Thank you Khayyam

Thorsen .. your very welcome .. you should now [mark the thread as [SOLVED]](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6)

best .. k

---

