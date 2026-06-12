---
title: "Bash script won't launch more than one program"
date: 2011-10-07
forum: General Help
---

### Post by mariodab on 2011-10-07
I am needing to launch more than one application at one time. I have a dual screen setup with my tv.  They are set to separate X displays.  What I am tying to do is get xbmc to start up on the TV fullscreen without locking the keyboard and mouse to the application. In order to do this i have to us wmctrl.  

So first I want to lauch xbmc in windowed mode, then I want to launch wmctrl to make it fullscreen without locking keyboard and mouse to the application and still use the other monitor to run other applications while xbmc runs on the tv.

I can successfully do this by manually launching xbmc then executing "wmctrl -x -r xbmc.bin.xbmc.bin -b toggle,fullscreen" in a terminal. xbmc goes to full screen and the keyboard and mouse can still be used with my primary monitor.

When I put this into a bash script it lauches xbmc then closes it out. Here is what I have

#!/bin/sh
xbmc &

sleep 10

wmctrl -x -r xbmc.bin.xbmc.bin -b toggle,fullscreen &

I thought maybe something was getting wonky with wmctrl so I tried a different application instead.  I got the same problem, when the second application tried to launch it canceled out both applications and nothing gets launched if I don't use the sleep command. If I do use the sleep command, the first application launches and then is terminated after the countdown.

It should be simple to launch more than one app.

prog1 &
prog2 &

But this doesn't work. Can anyone shed some light?

EDIT

Nevermind. I just used a launcher to point to the script and it did what it was supposed to do.

---

### Post by jwbrase on 2011-10-07
Don't put & after the last command in the script. 

If you do, the shell interpreting the script goes past that command, thinks "oh, this is the end of the script. I can close", and exits, taking all the programs launched in the script with it.

This will also happen if you close the last program launched: the shell will find itself at the end of the script and exit, taking previous programs in the script with it.

You may also be able to something with the "disown" builtin, which disassociates jobs from a shell, but I don't have a lot of experience with it.

So try:

```
program1 &
program2
```

or 

```
program1 &
disown %%
program2 &
disown %%
```

"%%" is shorthand for the last job launched.

---

