---
title: "Opening File Manager endlessly creating in programs bar. Can't stop it. Please advise"
date: 2010-03-08
forum: General Help
---

### Post by MadnessRed on 2010-03-08
When I turn on my computer I am greeted by an unending stream of "Starting File Managers" appearing in the programs list. This cannot be stopped, though none of the file managers actually open. They just sit there filling up my programs bar and wasting my cpu slowing down computer. It also means I cant upon my own folders, or see what programs I have open.

If I run terminal, type xkill and click on one of the buttons in the programs list, that kills them all, and I can see my programs again for a bit, until it fills up again. The panel disappears and appears again, with all the spawning messages gone and any other programs I have open remain there. Its just the randomly spawned "Starting File Managers" that don't come back.


My CPU fluctuates. Its around 60% to 90% load, when it should be idle, but is instead opening all these windows.
When I view the processes the most CPU intensive (when I sort) is Gnome System Monitor at 6% and then Gnome panel at 5%,

gconfd-2 is as around 2%,  compiz.real, dbus-deamon hover around 1%. And everything else is generally at 0%.

So somewhere, a hidden process is using about 70% of my CPU load. Which isn't shown in system-monitor. Maybe because its an admin process and I can only see simple user processes. I dunno.

There is something else though. I have a process with no name appearing, its blank. And it keeps disappearing and re-appearing. So you can hardly select it hard enough to kill it. I managed to kill it once and it said error, process (large number, 10,000 or 100,000) does not exist. So can't be killed.

When I do an xkill the console writes:
```
anthony@Anthony-Acer:~$ xkill
Select the window whose client you wish to kill with button 1....
xkill:  killing creator of resource 0x1600003
anthony@Anthony-Acer:~$ xkill
Select the window whose client you wish to kill with button 1....
xkill:  killing creator of resource 0x400003
anthony@Anthony-Acer:~$ xkill
Select the window whose client you wish to kill with button 1....
xkill:  killing creator of resource 0x400003
anthony@Anthony-Acer:~$ xkill
Select the window whose client you wish to kill with button 1....
xkill:  killing creator of resource 0x400003

```
It always ends in 0's then 3. And the number tends not to change that much.

I have tried moving things out of system>preferences>startup applications and ~/.config/autostart but to no avail, excpet getting funny themes, no gnome do or screenlets and no wallpaper.

I would greatly appreciate some help with this. If it were windows I would say it was a virus, but I have never heard of that in linux. Seems like a while-loop thats not being ended. Maybe the folder view opening is the condition for the while loop or something.

Anyway I will keep digging, see if I cant find any more info.

Thanks


Anthony

---

### Post by MadnessRed on 2010-03-08
ok, its odd how you can spend a whole day trying to fix something, get home, post asking for help and fix it yourself 5 mins later.

The problem was that I had turned off icons in gconf-editor on the desktop. And re-enabling them sorted it for some reason. Next question, why? As I quite like a clean icon free desktop. And if I do want icons I have a screenlet to emulate the KDE folder view.

---

