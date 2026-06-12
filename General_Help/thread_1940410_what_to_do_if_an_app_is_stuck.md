---
title: "what to do if an app is stuck?"
date: 2012-03-13
forum: General Help
---

### Post by jekylhyde on 2012-03-13
Hi
what to do if an app is stuck?
in windows i usually pressed ctrl+alt+del

---

### Post by ubudog on 2012-03-13
You can press CTL+ALT+F1, login with your username and password:
[hostname] login: myusername
Password: mypassword

Then do: 
```
ps ax | grep -i nameofapp
```

Find the 'PID' (number on the far left) and do: 
```
kill -9 PIDTHATYOUFOUND
```

Then to exit, do:
```
exit
```

And press CTL+ALT+F7, or CTL+ALT+F8 if that doesn't work.

Best of luck,
ubudog

---

### Post by LewisTM on 2012-03-13
The easiest and most fun is to create a new keyboard shortcut, bind it to somehting like Ctrl-Alt-Esc and command [FONT="Courier New"]xkill[/FONT].

Then invoke it and kill the window with the mouse. Sadly there's no sound effect but that could be remedied ;-)

Cheers!

---

### Post by ubudog on 2012-03-13
> **LewisTM said:**
> The easiest and most fun is to create a new keyboard shortcut, bind it to somehting like Ctrl-Alt-Esc and command [FONT="Courier New"]xkill[/FONT].

Then invoke it and kill the window with the mouse. Sadly there's no sound effect but that could be remedied ;-)

Cheers!

+1
:guitar:

Another way to do it would be the System Monitor, just search for it in the Dash, or on older Ubuntu releases (10.10 and below), System>Administration>System Monitor.  Click on the 'Processes' tab, find the process, press the End Process button, and enjoy. ;)

---

### Post by winh8r on 2012-03-13
Or use 

```
htop
```

select process, hit F9, hit enter

---

### Post by jekylhyde on 2012-03-13
> **LewisTM said:**
> The easiest and most fun is to create a new keyboard shortcut, bind it to somehting like Ctrl-Alt-Esc and command [FONT="Courier New"]xkill[/FONT].

Then invoke it and kill the window with the mouse. Sadly there's no sound effect but that could be remedied ;-)

Cheers!

i can't add shortcuts
settings manager > keyboard > application shortcut
i click add
type the command
& it will not add

---

### Post by LewisTM on 2012-03-13
> **jekylhyde said:**
> i can't add shortcuts
settings manager > keyboard > application shortcut
i click add
type the command
& it will not add
Well that ain't right... Maybe the shortcut you entered was already in use. Did you try other key combinations?

---

### Post by jekylhyde on 2012-03-13
> **LewisTM said:**
> Well that ain't right... Maybe the shortcut you entered was already in use. Did you try other key combinations?

maybe i'm not doing it right?
i have a place for the command but not for the shortcut
after i add the command i get a red X

---

### Post by LewisTM on 2012-03-13
Never seen that. Can you post a screenshot?
After entering the command (xkill), click OK and then enter the desired keystrokes in the next dialog.

---

### Post by Paqman on 2012-03-13
Alt-F2 > xkill > click > job done.

---

### Post by jekylhyde on 2012-03-13
> **LewisTM said:**
> Never seen that. Can you post a screenshot?
After entering the command (xkill), click OK and then enter the desired keystrokes in the next dialog.

LOL :p
when i clicked "print screen" to show you guys the problem
it says that it cant bind it to that key LOL
i always clicked cancel in this dialog because it seemed a dead end :lolflag:

note to the coders: write in this window some text... "click your new shortcut now"... something......
thanks

---

### Post by GreatDanton on 2012-03-19
go under:

applications<accesories<screenshot    (thats the program called in xubuntu, if you want to do the screenshot).
You can also download program called Shutter which has a little more options.

Enjoy
Great Danton

---

