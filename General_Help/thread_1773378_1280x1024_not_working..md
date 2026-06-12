---
title: "1280x1024 not working."
date: 2011-06-02
forum: General Help
---

### Post by justinjstark on 2011-06-02
The default resolution of my 19" monitor is 1280x1024 and it is a 5:4 monitor.  1280x1024 worked fine in 10.10.  I installed 11.04 from scratch.  The ubuntu splash screen is not centered (as if it is a 1280x1024 splash positioned on a smaller resolution).  Also, the resolution has defaulted to 1024x768 (4:3) and there is no option in the monitors dialog to go higher than that.

---

### Post by I'mGeorge on 2011-06-02
have you installed your video card specific drivers ?

---

### Post by justinjstark on 2011-06-02
> **I'mGeorge said:**
> have you installed your video card specific drivers ?

I have an intel graphics card.  Do I need to install anything to get it to work?

---

### Post by justinjstark on 2011-06-02
```
$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0 +   75.0  
   1152x864       75.0  
   1024x768       75.1     60.0* 
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  

```

---

### Post by justinjstark on 2011-06-02
Also, running ```
xrandr -s 1280x1024
``` sets the resolution but the window manager died and there are drawing errors all over the screen.  Anybody have any ideas what is going on?  Or am I just going to have to go back to 10.10?

---

### Post by justinjstark on 2011-06-02
Now going into monitors, it shows me having a 17" Dell as well as a laptop display.  What I really have is a 19" samsung.  What the heck is going on?

Edit: So here is what was happening.  X thinks I have two monitors, a laptop display and a 17" monitor.  By default, it was set to mirror screens.  Therefore, the highest resolution I could set was that of the nonexistent laptop display.  By doing ```
xrandr -s 1280x1024
```, it broke it out of mirror screens and changed the resolution of my "17 inch Dell" to 1280x1024.  So the question is, why is X seeing 2 screens (both incorrect) and how do I get it to see my one correct screen?

---

### Post by webofunni on 2011-06-02
are you able to detect the screen using gnome-display-properties

---

### Post by justinjstark on 2011-06-02
> **webofunni said:**
> are you able to detect the screen using gnome-display-properties

It detects a 17" dell and a laptop monitor.  I only have a 19" samsung.

---

### Post by webofunni on 2011-06-02
Gnome stores display properties in a file. Delete that and press detect again. 

```

rm ~/.config/monitors.xml

```

what 

```

xrandr --auto

```

is that able to do anything ?

Also what happens, If you switch off the display with less resolution ? or increase the resolution of one that supports more ?

```

xrandr --output VGA1 --mode 1280x1024

```

---

### Post by justinjstark on 2011-06-02
> **webofunni said:**
> Gnome stores display properties in a file. Delete that and press detect again. 

```

rm ~/.config/monitors.xml

```

what 

```

xrandr --auto

```

is that able to do anything ?

Nope.  Even after restarting, the monitors.xml file is still gone but I have the same problem.

> Also what happens, If you switch off the display with less resolution ? or increase the resolution of one that supports more ?

```

xrandr --output VGA1 --mode 1280x1024

```

The screen goes to 1280x1024.  Either the smaller resolution laptop display gets placed over top of the 1280x1024 display causing my resolution to be proper size but my desktop area to only be the size of the laptop resolution, OR the laptop display gets moved offscreen and my actual screen is 1280x1024 with lots of drawing errors.  I took a screenshot of what is happening.  The right hand side is what I actually see (with a lot of drawing errors) while the unity bar disappears (moves to the laptop screen which I cannot see).

---

### Post by justinjstark on 2011-06-02
I think I am going to go back to 10.10.  I like the old gnome better than unity anyway and 10.10 works without a hitch.

---

### Post by webofunni on 2011-06-02
I never faced any problem with new version. I am confused with the screen shot but. Do you really see two desktops in one monitor or do you have morethan one monitor ?

---

### Post by justinjstark on 2011-06-02
> **webofunni said:**
> I never faced any problem with new version. I am confused with the screen shot but. Do you really see two desktops in one monitor or do you have morethan one monitor ?

I just have one monitor, a 19" samsung.  Sometimes, it looks like it is trying to put both displays on the one monitor, other times, it moves the laptop display off the visible screen as in the previous screenshot.

I just installed 10.10 and it is working fine.  It is also calling my monitor a 17" Dell.  So it looks like 11.04 detects my monitor but it also falsely detects a laptop monitor and does some screwy things.

---

### Post by cracker89 on 2011-06-02
> **justinjstark said:**
>   i like the old gnome better than unity anyway and 10.10 works without a hitch.

+1

---

### Post by webofunni on 2011-06-04
Did they give you a dell monitor with samsung label ;-) 

Anyway, glad to know its working

---

### Post by justinjstark on 2011-06-04
> **webofunni said:**
> Did they give you a dell monitor with samsung label ;-)

Perhaps.  They also must have stretched it 2 inches while applying the Samsung label.

---

### Post by webofunni on 2011-06-04
Yeah, you are lucky :-)

---

### Post by Gidskid on 2011-06-04
I have this similar problem in that when i install ubuntu from fresh, it works but as soon as you reboot, the monitor says not supported?

G

---

### Post by webofunni on 2011-06-04
If you are able to get in to the console, execute 

xrandr

and see, if system is able to see the monitor

---

### Post by Gidskid on 2011-06-04
I can't get any further than the bios. Is there a shortcut to boot into the terminal mode?


G

---

### Post by webofunni on 2011-06-04
If that just bios, then problem is with something else.

To get in to the console. after finish booting, press CTRL + ALT + F1

---

