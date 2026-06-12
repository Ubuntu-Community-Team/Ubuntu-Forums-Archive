---
title: "Need help writing Xephyr script"
date: 2011-04-18
forum: General Help
---

### Post by Adrastus on 2011-04-18
[SIZE=3][FONT=Arial]Hi all,

I've only ever written one or two simple bash scripts before but how hard could it be, right? :P

I'd like to make a script that will launch an Xephyr window of a specific size with a window manager, an xterm, and Google Chrome running in it.

So far I have:
[/FONT][/SIZE]```
#!/bin/bash
Xephyr :100 -screen 790x590 &
DISPLAY=:100 xterm&
DISPLAY=:100 icewm &
DISPLAY=:100 google-chrome &
```[SIZE=3][FONT=Arial]

But it doesn't work.  All I get is the Xephyr window, nothing else will launch.  It works fine if I just run the DISPLAY... commands from a terminal window but I can't automate it with the script.  I get the sense that this is a newbie mistake in understanding the ways scripts are supposed to work but I haven't the faintest idea how to get it to do what I want.

Any bash gurus out there care to give some advice?

--Adrastus

[/FONT][/SIZE]

---

### Post by ~Plue on 2011-04-18
not sure why that doesn't work...try using a double ampersand after the xephyr line. that would make the other commands wait till xephyr is  loaded

or, another way to do the same thing would be to startx using an xinit script with xephyr;
```

#!/bin/bash[FONT=monospace]
[/FONT]xterm &[FONT=monospace]
[/FONT]google-chrome &
exec icewm
```make it executable and run
```
startx /path/to/file -- /usr/bin/Xephyr :100 -screen 790x590
```hope that helps

---

### Post by Adrastus on 2011-04-18
[FONT=Arial][SIZE=3]The double && worked!

Thanks!
[/SIZE][/FONT]

---

### Post by Adrastus on 2011-04-18
[FONT=Arial][SIZE=3]Hang on, I lied.
[/SIZE][/FONT]
```
#!/bin/bash
Xephyr :100 -screen 790x590 &&
DISPLAY=:100 xterm &
DISPLAY=:100 icewm &
DISPLAY=:100 google-chrome &
```

[SIZE=3][FONT=Arial]launches Xephyr with chrome but no window manager and not xterm.  Odd...[/FONT][/SIZE]

---

### Post by ~Plue on 2011-04-19
try the other method in my previous post. its a little more direct way to start a separate display than using a single script to run xephyr and then the other applications

---

### Post by Adrastus on 2011-04-19
[SIZE=3][FONT=Arial]Plue,

Starting Xephyr more like a new X session with the other script as a parameter worked great!  Thanks again.

By the way, to anyone else who looks at this, this is my solution to dictating which monitor fullscreen flash applications take place in while running a multi-head setup.  I know there have been some difficulties with this and using Xephyr seems to work.
[/FONT][/SIZE]

---

