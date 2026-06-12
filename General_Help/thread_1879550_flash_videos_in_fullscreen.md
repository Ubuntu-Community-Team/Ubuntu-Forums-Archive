---
title: "flash videos in fullscreen"
date: 2011-11-11
forum: General Help
---

### Post by sonnenwende93 on 2011-11-11
How do I get flash videos (youtube) to go full screen on a specific monitor? I have a dual monitor system and the videos are defaulting to my smaller screen. This is in 11.10, but I had the same problem in the previous version.

---

### Post by pqwoerituytrueiwoq on 2011-11-11
pause the video
open a terminal
move terminal to the monitor you want
run this long command 
```
d="`date`";ln -s `f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"` /tmp/"movie-$d";totem --fullscreen /tmp/"movie-$d"
```for some unknown reason this will not work via launcher/script

at the very least you will get hardware acceleration this way

---

### Post by sonnenwende93 on 2011-11-11
No luck! I get this:

```
sonne@HIVE:~$ d="`date`";ln -s `f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"` /tmp/"movie-$d";totem --fullscreen /tmp/"movie-$d"
ls: cannot access 6006/fd: No such file or directory
Segmentation fault

```

---

### Post by pqwoerituytrueiwoq on 2011-11-11
> **sonnenwende93 said:**
> No luck! I get this:

```
sonne@HIVE:~$ d="`date`";ln -s `f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"` /tmp/"movie-$d";totem --fullscreen /tmp/"movie-$d"
ls: cannot access 6006/fd: No such file or directory
Segmentation fault

```
is it a html5 video or a flash video?
that command only work with flash ones
that output is odd
*ls: cannot access 6006/fd: No such file or directory*
should be [FONT="Courier New"]ls /proc/6006/fd[/FONT]

---

### Post by sonnenwende93 on 2011-11-12
It's on Flash videos only (HTML5 is constrained in the browser for some reason?). A lot of the videos on youtube are flash only though. 

I can full screen video from VLC and other programs and it goes to the correct screen. I don't understand why flash is different.

---

### Post by sonnenwende93 on 2011-11-13
[https://bugbase.adobe.com/index.cfm?event=bug&id=2908816](https://bugbase.adobe.com/index.cfm?event=bug&id=2908816)

Adobe says this bug is fixed in future releases. So now I wait.

---

