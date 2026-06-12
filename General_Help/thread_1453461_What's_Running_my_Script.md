---
title: "What's Running my Script?"
date: 2010-04-13
forum: General Help
---

### Post by Penguin Guy on 2010-04-13
**EDIT:** Found it in [FONT="Courier New"]/usr/gdm/PostSession/Default[/FONT].

I made a python script to change my desktop background to a new random background, after a bit of fiddling around with various methods of automatically running the script I finally decided I'd just put a launcher on my desktop. However it appears that some remnant of my meddlings remains and persists in running my script when I restart my computer (although, for some reason, it only does this about 1/3 of the time).

I would like some way of finding the path to the program that is running running my script. My attempt fails:

**[BASH]**
[PHP]
#!/bin/bash
PARENT="`ps -p ${PPID} `"
echo '+---------------------------------------~' >> "$HOME/randomize-background.out"
echo "${PARENT}" >> "$HOME/randomize-background.out"
echo '+---------------------------------------~' >> "$HOME/randomize-background.out"
randomize-background2 >> "$HOME/randomize-background.out"
echo '' >> "$HOME/randomize-background.out"
[/PHP]
**[OUTPUT] *(comments added)***
```

*# test run:*
+---------------------------------------~
  PID TTY          TIME CMD
 4521 pts/0    00:00:00 bash
+---------------------------------------~
'Frozen Sun.jpg' is your new wallpaper.

*# real thing:*
+---------------------------------------~
  PID TTY          TIME CMD
 3365 ?        00:00:00 Default
+---------------------------------------~
*# <background-randomizer fails because gconf has already shut-down>*

```

Anyone got any ideas?

---

