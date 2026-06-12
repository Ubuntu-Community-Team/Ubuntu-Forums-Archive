---
title: "bash for programs running in terminal"
date: 2011-08-09
forum: General Help
---

### Post by walruspanzer on 2011-08-09
Trying to write a script for desktop launchers that are adaptable to screen resolution. Ideally, the program should:
 
*1. Determine screen resolution:*
*if "a" use xdotool options window size 1305 x 869 px and move to 135,0*
*if "b" use xdotool options window size 1545 x 1019 px and move to 135,0 *
 
**2. Check if program running:**
**if no, open program, and use "a" or "b" placement options, focus window**
**if yes, focus window**
 
*3. Close script and leave program open (if possible). *
 
Problems arise when trying to use the script on programs that run from and hog the terminal
(e.g. brasero, gcalctool, nautilus)
 
Here the script will load the program, and nothing else (probably because it still occupies the terminal as it runs) 
 
```
 
gcalctool && xdotool search "calculator" windowmove 135 0 

```
 
This next command will cause the program to load, move, but it keeps focusing itself like xdotool is running the windowmove function constantly - it keeps focusing itself until script stopped. 
 
```
 
gcalctool & xdotool search "calculator" windowmove 135 0

```
 
This had the same effect as the above code, but seems to work as a conditional subscript running when the process is running in the terminal - it just goes infinitely. 
 
```
 
while [1] ; do xdotool search "calculator" windowmove 135 0 done exit 

```
 
Is there some kind of "if, then" or "while, do" or some kind of conditional I can put in to the script ensure the window is moved only once if the program is running within the terminal? Is there a way to remove the program from the terminal from the script once it's been called? 
 
Any help appreciated, thanks!

---

### Post by Vaphell on 2011-08-09
```
$ ps
  PID TTY          TIME CMD
 4267 pts/2    00:00:00 bash
 7188 pts/2    00:00:00 gcalctool
 7241 pts/2    00:00:00 ps

$ app=gcalctool
$ pid=$( pidof "$app" ); if [ "$pid" ]; then echo "$app is running"; else echo "$app is not running"; fi;
gcalctool is running

$ app=gimp
$ pid=$( pidof "$app" ); if [ "$pid" ]; then echo "$app is running"; else echo "$app is not running"; fi;
gimp is not running

```

this can't work
```
gcalctool && xdotool search "calculator" windowmove 135 0
```
second part (after &&) waits for finish of the first part, closing gcalctool that is.

single & at the end of command is used to put its process in the background so it doesn't block the terminal. You need to run program with & and proceed with your stuff in new line

---

### Post by walruspanzer on 2011-08-09
Thanks for the quick response! Your method of detecting running programs is much cleaner than mine. I'll definitely use it. Here is what I'm getting. 

```
#! /bin/bash

app=gcalctool
pid=$( pidof "$app" ); if [ "$pid" ]; then echo "$app is running"; else echo "$app is not running, start app" && 
$app & 
xdotool search "calculator" windowmove 135 0 ;
fi ;

```

I get this, xdotool runs but the window doesn't move and it returns to an open terminal. 

```
~$ bash ./Desktop/test.sh
gcalctool is not running, start app
Defaulting to search window name, class, and classname
~$

```

xdotool will move the program as is, only if initiated separately from the script. I'm trying to do both with one script. 

can you tell I'm new to this?

---

### Post by Vaphell on 2011-08-09
```

#!/bin/bash

app=gcalctool
pid=$( pidof "$app" );

if [ "$pid" ]
then
  echo "$app is running"
else
  echo "$app is not running, start app"
  $app & 
fi

sleep 1
wids=$( xdotool search --class "$app" )
for wid in $wids
do
  xdotool windowmove $wid 135 0
done

```

sleep seems to be required apparently or else windowmove part happens before windows are registered (thus nothing is found -> nothing happens). I had to use the for loop because i have an older version of xdotool than the one that supports your one-liner selecting and performing an operation at once.

---

### Post by walruspanzer on 2011-08-10
You made it look so simple! My program was a mess in comparison. I'm still tweeking the program, but here's a rough idea of what I'm working with so far. It works for programs that hog the terminal, and for programs with window class names that are the same as the application name like gimp and gcalctool.  I'm using the script to make smart and adaptive program launcher screenlets (that change size parameters based on resolution). Thanks a bunch! 
 
 
```
app=rhythmbox
 
 
externaldisplay="backend: nvidia
associated displays: CRT-0, DFP-0
metamode: CRT-0: 1680x1050 @1680x1050 +0+0
scaling: default, default
xinerama info order: CRT-0, DFP-0"
 
 
pid=$( pidof "$app" );
 
if [ "$pid" ];
 
then
 
 echo "$app already in progress, adapting to current resolution" 
 
#       COMMAND TO BRING WINDOW TO FOCUS (maybe resize window)
 
else
 
 echo "$app is not running, initiate and adapt to current resolution"
  
 $app & 
  
fi
 
 
sleep 1
 
wids=$( xdotool search --class "$app" )
gen=$( xdotool search "$app" )
 
for wid in $wids
 
do 
if [ "`disper -p`" = "$externaldisplay" ]; 
then
 
 xdotool windowmove $wid 135 0 && xdotool windowsize $wid 1545 1019 &&
 
 echo "ADJUST TO EXTERNAL"
 
else 
 
 xdotool windowmove $wid 135 0 && xdotool windowsize $wid 1305 869 &&
 
 
 echo "ADJUST TO LAPTOP SCREEN"
 
fi
 
done

```

---

### Post by Vaphell on 2011-08-10
not that important but you should use $() instead of backticks ``

---

