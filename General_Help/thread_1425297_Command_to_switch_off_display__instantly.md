---
title: "Command to switch off display  instantly ???"
date: 2010-03-08
forum: General Help
---

### Post by linuxyogi on 2010-03-08
Hi, ):P

IS THERE ANY COMMAND WHICH WILL SWITCH OFF THE DISPLAY IMMEDIATELY ?

Sometimes, while listening to music, downloading a file I don't need the display.

I know about the Gnome Power options. The minimum time available there is 1 min.

I need a command which which will put the display to sleep instantly.

Please reply.

---

### Post by polki@mac.com on 2010-03-09
It's not exactly what you're looking for, but ctrl + alt + l works for me. It kicks in my screensaver. Maybe try it with yours set to blank screen?
Hope you find a solution.

---

### Post by stinkeye on 2010-03-09
If it's activating the screensaver your after, the command is:
```
gnome-screensaver-command --activate
```

---

### Post by asmoore82 on 2010-03-09
You could try this with _***[COLOR="Red"]extreme caution[/COLOR]***_

Before trying it, you should probably set some keyboard shortcut to:
```
xrandr --auto
``` ^^and test that

Then, you could try this:
```
[COLOR="Red"]#with _**[U]*extreme caution*_**[/U]
xrandr --output LVDS --off[/COLOR]
```^^"output" may need to be "LVDS1" or "default"

[COLOR="Red"]******You will need that keyboard shortcut to turn the screen back on!!***[/COLOR]

---

### Post by linuxyogi on 2010-03-09
> **asmoore82 said:**
> You could try this with _***[COLOR="Red"]extreme caution[/COLOR]***_

Before trying it, you should probably set some keyboard shortcut to:
```
xrandr --auto
``` ^^and test that

Then, you could try this:
```
[COLOR="Red"]#with _**[U]*extreme caution*_**[/U]
xrandr --output LVDS --off[/COLOR]
```^^"output" may need to be "LVDS1" or "default"

[COLOR="Red"]******You will need that keyboard shortcut to turn the screen back on!!***[/COLOR]

What do you mean by "extreme caution" ? 

What are the risks ?

Are you saying that if something goes wrong, even restarting the computer won't undo the changes made by the command ? If so. I guess a full OS reinstallation will be too much. 

Please reply.

---

### Post by linuxyogi on 2010-03-11
> **polki@mac.com said:**
> It's not exactly what you're looking for, but ctrl + alt + l works for me. It kicks in my screensaver. Maybe try it with yours set to blank screen?
Hope you find a solution.

> **stinkeye said:**
> If it's activating the screensaver your after, the command is:
```
gnome-screensaver-command --activate
```

Finally I found the solution !!!!:D & that too in this very forum !!!


I guess I didn't search properly.

The command is ----

xset dpms force suspend

Thanks for trying to help. Bye.

---

### Post by asmoore82 on 2010-03-11
> **linuxyogi said:**
> xset dpms force suspend
Quoted for sheer Awesomeness

Thank you!

---

