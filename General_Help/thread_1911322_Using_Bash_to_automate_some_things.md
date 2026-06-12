---
title: "Using Bash to automate some things"
date: 2012-01-18
forum: General Help
---

### Post by bcampbe81 on 2012-01-18
Hi All

I am completely new to bash scripting and feel like this should be a fairly easy task, however very few of the tutorials I have looked into are helping all that much.

I managed to find a script previously that would open a terminal then run a program in the terminal. I since then have managed to misplace this script (probably due to my pc breaking).

So basically what I was trying to do was

Right Click on my 'Desktop' > Scripts > Scriptinquestion
Open a terminal
CD /media/DumpDrive/DumpFolder
Vobcopy -m

I've got 8 seasons of scrubs on dvd just sitting there waiting for me to backup to my drive for watching on my WD Live TV Streaming device.

So far i have
```

#!/bin/bash
gnome-terminal

```

which is not much i know

Any help would be massively appreciated
Ben

---

### Post by bcampbe81 on 2012-01-18
well i made some progress

I have managed to make the script start the process that I wanted but I was after it to happen in a terminal to see what was actually happening.

Any help with making a program run in a terminal using a script?

---

### Post by Habitual on 2012-01-18
/usr/bin/gnome-terminal -e "/path/to/script.sh"

---

