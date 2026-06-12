---
title: "Wanna create a workaround script (press F3)"
date: 2012-02-20
forum: General Help
---

### Post by ggimp on 2012-02-20
I'm having problems with my graphicscard (hd6470) and I have read many guides but there is no real solution out there yet. 
So I'm wondering if you could help me build a script that simulates 3 press on F3. 
I wanna put this script in startup so that my screen lights up automatically on startup.

I'm a complete newbie in ubuntu so be gentle.

---

### Post by Vaphell on 2012-02-20
install xdotool
```
sudo apt-get install xdotool
```

send F3
```
xdotool key F3
```

---

### Post by ggimp on 2012-02-20
Let me see if I got this right.

I installed xdotool and I tried to run the command by pressing alt F2 and the type in "xdotool key F3". 
I didn't see any result. The display didn't light up. Am I doing something wrong or is it possible that the F3 simulation doesn't really work with the shortcut function. (F3 means light up on this keyboard)

---

### Post by Vaphell on 2012-02-21
imo you are not doing anything wrong
open terminal and simulate various key combinations. You can see that xdotool key a will create 'a', F10 will bring the menu, key F11 will do fullscreen (at least they do than in my 10.04) and ctrl+shift+v will paste stuff from ctrl+c buffer (ctrl+shift+c in terminal, ctrl+c terminates program)

it is possible that f3 does some hardware based voodoo and the system simply doesn't know about it.

xdotool can also simulate holding and releasing the key (keydown, keyup) though i doubt it will help

---

