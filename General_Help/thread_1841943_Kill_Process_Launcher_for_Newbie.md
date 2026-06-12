---
title: "Kill Process Launcher for Newbie"
date: 2011-09-10
forum: General Help
---

### Post by Quarkrad on 2011-09-10
_Running 10.10_   A number of times I close Thunderbird but find on a re-launch I cannot do it because 'the process is already running'.  So I have to go System/Admin/System Monitor and manually kill the Thunderbird process.  Can I right click on the Desktop and create a launcher that contains a script that will kill the Thunderbird process for me rather than having to do it via System Monitor? What txt would I put in the Command?

---

### Post by Triblaze on 2011-09-10
I'm pretty sure you could just enter this in the command line:

```
kill thunderbird
```

Try that

---

### Post by Quarkrad on 2011-09-10
Afraid that doesn't work.  I would like an icon on my Desktop/Cairo Dock so that when I double click (or single click from Cairo Dock) it kills the Thunderbird process.

---

### Post by Quarkrad on 2011-09-13
Bump - it would be nice to have an icon on my Desktop that I could double click that would kill the Thunderbird process.

---

### Post by Quarkrad on 2011-09-17
Bump

---

### Post by community on 2011-09-17
You may run the following command in terminal to get an application_ID
pidof Thunderbird
Now you get a number.Then use that number to kill the process.
kill application_ID


Note:Your Thunderbird command should bet the correct one.Use the exact command for the same.

---

### Post by Quarkrad on 2011-09-19
Thank you - but does not the ID change every time you launch an instance of Thunderbird?  What I would like is an icon in my Cairo Dock that I can click on that will kill the Thunderbird process.  It is looking to me that maybe this is not possible.

---

### Post by Quarkrad on 2011-09-25
bump

---

### Post by debd on 2011-09-25
use 
```
killall thunderbird
```but why'd you need to kill it?
is thunderbird minimized to the tray when you click 'close'?
thunderbird'd generally quit on a click on the 'close' button, but there's a add-on to let it do otherwise i.e. minimize to the tray on close.
Try File > Quit in thunderbird.

otherwise you can use :
```
ps -e|grep thunderbird|cut -c 2-5|xargs kill
```This will always fetch the process id of all currently running instances of thunderbird and kill them.

If that doesn't work somehow, use:
```
ps -e|grep thunderbird|cut -c 2-5|xargs kill -9
```If you want a script, just put in the command in a text file like this

```
#!/bin/bash

ps -e|grep thunderbird|cut -c 2-5|xargs kill
```save it in home directory as something.sh 
make it executable: ```
chmod u+x ~/something.sh
```and create a shortcut for it in whatever dockbar you use.

---

### Post by Quarkrad on 2011-09-26
Many thanks -solved.   Thunderbird was not in Tray - it closes down but sometimes I cannot re launch because the Process is still running.  This kills it with one click.

---

