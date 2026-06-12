---
title: "Software to turn off screen"
date: 2011-04-09
forum: General Help
---

### Post by mrnettles on 2011-04-09
Hello,
does anyone know if there's a piece of software to turn off the screen or turn on a screensaver from a keyboard control? At the moment I have to switch between different power modes to either leave the screen on for watching videos, or wait for a minute when I want it off.

Thanks.

---

### Post by Thewhistlingwind on 2011-04-09
You mean off as in *off* or as in locked? Cause you can press Ctrl, alt, L and pretty much get that result.

---

### Post by mendhak on 2011-04-09
Hi, put this in a script file:

xset dpms force off


Then, in your Keyboard Shortcuts, you can add a new command to

bash /home/mrnettles/scripts/screenoff.sh

Make sure screenoff.sh is set to executable, and has 

#!/bin/bash

at the top.

HTH

---

### Post by mrnettles on 2011-04-15
Whistlingwind, I mean just to blank the screen without locking it.

Mendhak, thanks, I tried that, but nothing happened when I pressed the new shortcut. I don't really know what I'm doing, to be honest, but I looked up scripts here:

[http://www.ax697.org/writing-a-basic-ubuntu-script-200786.html](http://www.ax697.org/writing-a-basic-ubuntu-script-200786.html)

---

### Post by mrnettles on 2011-04-15
Ah, OK, I've got the script running from a keyboard shortcut but it comes straight back on again after a second or so. Progress though!

---

### Post by stinkeye on 2011-04-15
> **mrnettles said:**
> Ah, OK, I've got the script running from a keyboard shortcut but it comes straight back on again after a second or so. Progress though!
Use this as the command in your keyboard shortcut.
The delay stops it from registering the upstroke and turning your screen back on.
```
bash -c "sleep 1 && xset dpms force off"
```

---

### Post by spirit.986 on 2011-04-15
On my laptop [ASUS M51Va]("http://www.drivers-xp.com/asus/asus-m51va-windows-xp-drivers-download/") i can turn the the screen off the same way like i was doing it on windows... **[Fn] + [F7]**... 
Most of those Function keys work too :)

---

### Post by pqwoerituytrueiwoq on 2011-04-15
The screen saver will turn the screen back on just so you know
there is a inhibit command to stop the screen saver from coming on
i would post it but i only have it on my laptop as i do not need it on my desktop

---

### Post by mrnettles on 2011-04-19
> **stinkeye said:**
> Use this as the command in your keyboard shortcut.
The delay stops it from registering the upstroke and turning your screen back on.
```
bash -c "sleep 1 && xset dpms force off"
```


That seems to work, thanks very much.

---

### Post by stinkeye on 2011-04-19
> **mrnettles said:**
> That seems to work, thanks very much.
No problem.
Also the command to turn on the screensaver is
```
gnome-screensaver-command --activate
```

---

### Post by mrnettles on 2011-04-20
Aha, it does work turning it off, but as pqw says, it turns back on after whatever time the screensaver is set for. Any ideas?

---

### Post by mrnettles on 2011-04-20
Hmm, no, it doesn't seem to be the screensaver time, as I just set that to 2  hours. The screen turns back on after about a minute. Mystery to me.

---

### Post by mrnettles on 2011-04-28
Surely there must be a way to do this? I've installed Dell hotkeys but it doesn't seem to work. I've just gone back to the 1-minute screensaver for now. Sigh.

---

### Post by pqwoerituytrueiwoq on 2011-04-28
what i did was had the script open a terminal window (run in terminal setting)
```
#!/bin/sh
sleep 1
xset dpms force off
gnome-screensaver-command --inhibit
```wish i knew a better way to do that 
better as in does not open a window (window is required if you want your screen saver to work after running script)
edit:
anyone know how to detect idle/active from the terminal
if i knew that i think  i can make a better one

---

