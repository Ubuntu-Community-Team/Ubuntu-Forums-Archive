---
title: "Application missing from GNOME menu?"
date: 2011-06-30
forum: General Help
---

### Post by eskmsaul on 2011-06-30
I downloaded mupen64plus from the software center the other day but I can't find it anywhere! Every other program shows up fine. I tried making a manual launcher and that failed too.... Software center says it is installed, but it simply doesn't show up!

---

### Post by jerrrys on 2011-06-30
do a search. and find the read me files.  also in terminal you can try **man mupen64plus**

---

### Post by eskmsaul on 2011-07-01
It's there....it says
saul@saul-laptop:~$ man 
What manual page do you want?
saul@saul-laptop:~$ mupen64plus
 __  __                         __   _  _   ____  _             
|  \/  |_   _ _ __   ___ _ __  / /_ | || | |  _ \| |_   _ ___ 
| |\/| | | | | '_ \ / _ \ '_ \| '_ \| || |_| |_) | | | | / __|  
| |  | | |_| | |_) |  __/ | | | (_) |__   _|  __/| | |_| \__ \  
|_|  |_|\__,_| .__/ \___|_| |_|\___/   |_| |_|   |_|\__,_|___/  
             |_|         [http://code.google.com/p/mupen64plus/](http://code.google.com/p/mupen64plus/)  
Mupen64Plus Console User-Interface Version 1.99.4

UI-console: attached to core library 'Mupen64Plus Core' version 1.99.4
            Includes support for Dynamic Recompiler.
Error: no ROM filepath given
saul@saul-laptop:~$

---

### Post by sam_delta on 2011-07-01
it looks like mupen64plus is a command line aplication (thats why you cant find it in the menus), to read the manual page, do as jerrys say'd (in the same prompt)
```
man mupen64plus
```

Looking at the output you provided, I assume that the usage of the program might be something like 
```
mupen64plus ROM_FILE
``` just replace ROM_FILE with the path of the game rom file you are trying to play

sam

---

### Post by sandman887 on 2011-07-01
You can also try this, to see if it's installed, and where:
```
which mupen64plus
```

You may have to start it from a terminal by invoking it with the command name.

---

