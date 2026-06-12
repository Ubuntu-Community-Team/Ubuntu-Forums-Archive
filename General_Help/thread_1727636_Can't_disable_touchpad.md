---
title: "Can't disable touchpad"
date: 2011-04-12
forum: General Help
---

### Post by kd4hey on 2011-04-12
Ubuntu 10.10

I tend to hit my touchpad while typing, so I prefer to disable it.  I had it disabled in 10.04, but after upgrading to 10.10 it doesn't seem to work anymore.

I also downloaded the g-pointing-devices & put a check in the Disable touchpad box.  This worked for a little while, then the touchpad starts working again, with the box still checked.

Any clues?

Thanks in advance for all replies.

---

### Post by vivek.pandey on 2011-04-13
hi
try this command
```

gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled false

```

---

### Post by rummy77 on 2011-04-13
I do this all the time by going into the terminal and using ```
synclient TouchpadOff=2
```

The variables you can use are:
0: touchpad is on and works like normal
1: touchpad is completely off
2: touchpad will move the pointer but will not tap-to-click

Also, when your touchpad is off, remember that Ctrl+Alt+T will get a terminal to turn it back on.

---

### Post by Krytarik on 2011-04-13
How about using the "Touchpad Indicator" applet, especially for you, rummy77, since you're apparently switching the modes regularly; however, the mentioned option "2" is not available:
[http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/](http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/)

Greetings.

---

### Post by vivek.pandey on 2011-04-13
> **Krytarik said:**
>  however, the mentioned option "2" is not available:
[http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/](http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/)

Greetings.
by "2" option do you mean my answer?
if yes then sir/mam this technique is working fine enough on my 10.10 system and OP too hAS 10.10 so it should work fine there too :-)

---

### Post by Krytarik on 2011-04-13
> **vivek.pandey said:**
> by "2" option do you mean my answer?
Nope, I was referring to *rummy77's* post:
> **rummy77 said:**
> 
2: touchpad will move the pointer but will not tap-to-click

Sorry, if that wasn't clear enough.

And yes, I assumed that your command works.

---

### Post by kd4hey on 2011-04-14
> **vivek.pandey said:**
> hi
try this command
```

gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled false

```

I have started with this solution.  Now if only it "sticks".  If later the touchpad goes back to working on it's own, I will try the next option.

Thanks so much for all the great responses.  This is what makes Ubuntu GREAT!!

---

### Post by rummy77 on 2011-04-14
> **Krytarik said:**
> How about using the "Touchpad Indicator" applet, especially for you, rummy77, since you're apparently switching the modes regularly; however, the mentioned option "2" is not available:
[http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/](http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/)


I'm not sure why, but I've used the touchpad indicator on my system before and it hasn't worked.  The indicator would remember my setting for a while, but then would stop working.  Because I'm using a synclient bash script for other touchpad settings, it's easy enough to use the terminal command to make quick and simple changes. I'll try the indicator again, though, and file a bug if it doesn't work.

Cheers.

---

### Post by kd4hey on 2011-04-14
> **kd4hey said:**
> I have started with this solution.  Now if only it "sticks".  If later the touchpad goes back to working on it's own, I will try the next option.

Thanks so much for all the great responses.  This is what makes Ubuntu GREAT!!

Well, Vivek's solution worked,....until I rebooted, then the touchpad is working again, so, I'll move on to Rummy's solution.

---

### Post by Enigmapond on 2011-04-14
One of these solutions should work for you. I tried them all and they work for me, (well the applet was quirky). If not...Duct Tape.. :D

---

