---
title: "Play script in terminal"
date: 2010-06-16
forum: General Help
---

### Post by Smart Viking on 2010-06-16
Hey, i have made a simple script to play music:

[I]#! /bin/bash

cd ~/rollingstones

play track??*wav[/I]


But when i execute it, it only plays the music in the background, and not in a terminal. How can i make it run in a terminal, so i can stop it without using the kill command, and go to next song by pressing ctrl+c?

Thanks. :)

---

### Post by inameiname on 2010-06-16
I have this in the front of a few of my scripts so it'll open in the terminal:

#!/bin/bash
tty -s; if [ $? -ne 0 ]; then gnome-terminal -e "$0"; exit; fi
(whatever is in the rest of the script)

Perhaps a variation of that? This one works perfectly for a screencasting script I use, which will stay open until I feel like stopping it, using 'q', for quit.

---

### Post by Smart Viking on 2010-06-16
> **inameiname said:**
> I have this in the front of a few of my scripts so it'll open in the terminal:

#!/bin/bash
tty -s; if [ $? -ne 0 ]; then gnome-terminal -e "$0"; exit; fi
(whatever is in the rest of the script)

Perhaps a variation of that? This one works perfectly for a screencasting script I use, which will stay open until I feel like stopping it, using 'q', for quit.

Thank you, that work perfectly, only had to replace gnome-terminal with xfce4-terminal. :D

---

### Post by inameiname on 2010-06-16
Cool. Glad I could help.

---

