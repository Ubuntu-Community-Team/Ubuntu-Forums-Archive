---
title: "Help me out with my Startup Bash Script"
date: 2011-04-30
forum: General Help
---

### Post by UltraZone on 2011-04-30
Since I installed 11.04, I want to change the behavior of launching Cairo-dock at start up.  Previously I had a simple startup entry as:

```
cairo-dock -o
```This worked perfectly until I upgraded; because 11.04 provides its own dock, I want now the Cairo Dock to launch only when the Ubuntu Classic environment is launched at startup, so I created this bash script to launch it, here's the code:

```
#!/bin/bash
#Check what session we're in
if [ $DESKTOP_SESSION = 'gnome-classic'] ; then
sleep 15
echo `cairo-dock -o`
fi

```But it doesn't work.  

When I actually execute this script from a terminal it lauches Cairo, however it doesn't work when I point to it with Startup Applications.... why?

---

### Post by Copper Bezel on 2011-05-01
Have you tried switching the DE check and the delay, and possibly extending the delay? It's possible that the script is actually launching before the session variable is set.

---

### Post by UltraZone on 2011-05-01
I increased the time up to 30 seconds, still nothing.

Thing is about the if statement is that it works, because when I actually execute the script from a terminal, it does indeed launch Cairo Dock.  But when it is executed from Startup Application, zip. ? huh? :confused:

---

