---
title: "How do I run a script on system startup?"
date: 2011-02-28
forum: General Help
---

### Post by Kumidan on 2011-02-28
I'm new both to the forum and to Linux world.
After I've installed Ubuntu I've found that the mouse pointer was slow even raising the speed and sensibility to the highest levels.
I've solved writing this command into the console

xset m 3 3

now I don't want to write it every time I start the system, is there a way to run that code automatically?

---

### Post by TeoBigusGeekus on 2011-02-28
Administration>Preferences>Startup Applications
Create a new entry and give as its command
```
xset m 3 3
```

---

### Post by blueridgedog on 2011-02-28
System -> Preferences -> Startup Applications, click add, then fill out the form as required, using your command as the command.

---

### Post by Kumidan on 2011-02-28
Thanks for the replies.
I've just tried and restarted the system, but it doesn't work, the mouse moves slowly, I've written again the command into the console and it is fast again.

---

### Post by TeoBigusGeekus on 2011-02-28
You probably need to add a sleep command to it.
Create a new text file and add these lines
```
#!/bin/bash
sleep 5
xset m 3 3
```
to it. Save it with any name you like and then
```
chmod +x nameofscript
```
to make it executable.
Change the command of your startup entry to
```
bash /path/to/script/nameofscript
```
Play with the value in the sleep command if it still doesn't work.

---

### Post by r.osmanov on 2011-02-28
If you want it for all users, place the bash script in */etc/init.d* and run
```
sudo update-rc.d [COLOR=DarkOrange]*your-script*[/COLOR] defaults
```**EDIT:** Probably, it's better to set the script sequence number greater than that for *x11-common*. See UPDATE-RC.D(8)(*man update-rc.d*).

---

### Post by Kumidan on 2011-02-28
> **TeoBigusGeekus said:**
> You probably need to add a sleep command to it.
Create a new text file and add these lines
```
#!/bin/bash
sleep 5
xset m 3 3
```to it. Save it with any name you like and then
```
chmod +x nameofscript
```to make it executable.
Change the command of your startup entry to
```
bash /path/to/script/nameofscript
```Play with the value in the sleep command if it still doesn't work.
Thanks, this works :)

---

