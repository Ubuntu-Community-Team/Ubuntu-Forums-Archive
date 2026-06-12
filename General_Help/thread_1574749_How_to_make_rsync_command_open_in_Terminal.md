---
title: "How to make rsync command open in Terminal?"
date: 2010-09-14
forum: General Help
---

### Post by nLinked on 2010-09-14
I have the following rsync command for making some backups:

```
rsync -r --progress --delete -H --numeric-ids -a --exclude=.gvfs /source /media/Backup
```

If I paste that in my Terminal, it will perform a backup of all the files and show me what's going on in the Terminal window.

But how can I make that into a launcher? I have made a launcher on my desktop with that code in its Properties, but double-clicking it starts the rsync process (I can see HDD activity) but a Terminal window won't open.

---

### Post by Richard1979 on 2010-09-14
Not tested, but try:
gnome-terminal 'rsync -r --progress --delete -H --numeric-ids -a --exclude=.gvfs /source /media/Backup'

or:
gnome-terminal `rsync -r --progress --delete -H --numeric-ids -a --exclude=.gvfs /source /media/Backup`

---

### Post by pbrane on 2010-09-14
1. create a new gnome-terminal profile called *backup*.

2. Open then terminal profile preferences for profile *backup*

3. in the **Title and Command** tab edit **run custom command instead of my shell** and enter your rsync command. - or you can put your rsync command in a shell script and enter that.

4. create a launcher and enter this as the command: **gnome-terminal --window-with-profile=backup**

---

### Post by Deadite81 on 2010-09-14
Another way is to create a shell script with
```
gnome-terminal -e
```before your command.  that should work with any command.  For example, create a new text file and name to "top" or "top.sh".  Then put this in it:
```

#!/bin/bash

gnome-terminal -e top
```Now right-click it and choose the "Properties" tab and make the file executable.  Double-clicking the file should launch a terminal with the program Top running in it.

If there are spaces in your command, ensure that after gnome-terminal -e your command is in quotes:

```
gnome-terminal -e 'sudo nethogs wlan0'
```Also, [bash alias]("http://ubuntuforums.org/showthread.php?t=1416864")es could be useful, but you have to have a terminal open to run one.

The best idea for a backup operation, in my opinion, is to use a [Cron]("http://clickmojo.com/code/cron-tutorial.html") [job]("http://ubuntuforums.org/showthread.php?t=102626") so you just don't have to worry about it.

---

### Post by nLinked on 2010-09-15
> **pbrane said:**
> 1. create a new gnome-terminal profile called *backup*.

2. Open then terminal profile preferences for profile *backup*

3. in the **Title and Command** tab edit **run custom command instead of my shell** and enter your rsync command. - or you can put your rsync command in a shell script and enter that.

4. create a launcher and enter this as the command: **gnome-terminal --window-with-profile=backup**

This method works! Would prefer the methods below but they are having problems...

> **Richard1979 said:**
> Not tested, but try:
gnome-terminal 'rsync -r --progress --delete -H --numeric-ids -a --exclude=.gvfs /source /media/Backup'

or:
gnome-terminal `rsync -r --progress --delete -H --numeric-ids -a --exclude=.gvfs /source /media/Backup`

> **Deadite81 said:**
> Another way is to create a shell script with
```
gnome-terminal -e
```before your command.  that should work with any command.  For example, create a new text file and name to "top" or "top.sh".  Then put this in it:
```

#!/bin/bash

gnome-terminal -e top
```Now right-click it and choose the "Properties" tab and make the file executable.  Double-clicking the file should launch a terminal with the program Top running in it.

If there are spaces in your command, ensure that after gnome-terminal -e your command is in quotes:

```
gnome-terminal -e 'sudo nethogs wlan0'
```Also, [bash alias]("http://ubuntuforums.org/showthread.php?t=1416864")es could be useful, but you have to have a terminal open to run one.

The best idea for a backup operation, in my opinion, is to use a [Cron]("http://clickmojo.com/code/cron-tutorial.html") [job]("http://ubuntuforums.org/showthread.php?t=102626") so you just don't have to worry about it.

These 2 methods both give problems. All that happens is Terminal will open, but the command won't enter itself in. It will just be  a normal terminal. Any ideas why? Did the above exactly.

---

### Post by Deadite81 on 2010-09-16
Just running "gnome-terminal" plus the command won't work.

As for using "gnome-terminal -e" plus the command, I use it on a regular basis, mostly in [mygtkmenu]("http://sites.google.com/site/jvinla/mygtkmenu") and shell scripts.

I have had problems with the "-e" modifier before with certain commands and have had to use a terminal profile instead.  It might be because of the symbols within the command, but I'm not versed enough in the terminal enough to spot the problem.

---

### Post by nLinked on 2010-09-16
> **Deadite81 said:**
> Just running "gnome-terminal" plus the command won't work.

As for using "gnome-terminal -e" plus the command, I use it on a regular basis, mostly in [mygtkmenu]("http://sites.google.com/site/jvinla/mygtkmenu") and shell scripts.

I have had problems with the "-e" modifier before with certain commands and have had to use a terminal profile instead.  It might be because of the symbols within the command, but I'm not versed enough in the terminal enough to spot the problem.

Thanks, but tried it exactly your way as well and it simply opens terminal as a normal terminal waiting for a command. It won't process the command. I did
```
gnome-terminal -e 'commands here'
```

If I enter the command in Run (alt + F2) and tick Run In Terminal, it will open with Terminal and run perfectly. Wonder what command Run is using. It does show the command it uses if you expand it, but doesn't show the Run In Terminal part.

---

