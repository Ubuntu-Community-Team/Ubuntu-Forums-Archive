---
title: "startup command didn't run?"
date: 2012-08-12
forum: General Help
---

### Post by LLCoolJeff on 2012-08-12
I recently did a clean install of xubuntu 12.04 and set up dual monitors, I had to run 
```
xrandr --output LVDS --left-of CRT1
```to get the monitors to display side by side correctly, and the tutorial I was reading said it will undo itself upon logout so I should add it to the "session and startup" commands.

I made a command that looked like this:

[IMG]http://i48.tinypic.com/fxdkj6.png[/IMG]

but the next time I logged out and logged back in, the monitors had reverted to the way they were before. I went back into where I typed the command and copied and pasted it into the terminal and it worked great, so why did it not run the command and work when I logged in?

THanks

---

### Post by sienile on 2012-08-12
Have you tried putting in the full path?

```
/usr/bin/xrandr --output LVDS --left-of CRT1
```

It shouldn't matter, but I have had some programs that pitched a fit if I didn't have the full path in the startup command.

---

### Post by LLCoolJeff on 2012-08-12
> **sienile said:**
> Have you tried putting in the full path?

```
/usr/bin/xrandr --output LVDS --left-of CRT1
```It shouldn't matter, but I have had some programs that pitched a fit if I didn't have the full path in the startup command.


Thanks for your reply...I tried what you said above and it did not work for me unfortunately...

Does anyone else have any ideas of how to get this to work on startup?

---

### Post by Toz on 2012-08-12
How about:
```
bash -c "xrandr --output LVDS --left-of CRT1"
```

Or, create a script that contains that code (~/xrandr_setup):
```

#!/bin/bash
xrandr --output LVDS --left-of CRT1
```
...make the script executable and reference the script in the autostart.

---

### Post by LLCoolJeff on 2012-08-12
> **Toz said:**
> How about:
```
bash -c "xrandr --output LVDS --left-of CRT1"
```Or, create a script that contains that code (~/xrandr_setup):
```

#!/bin/bash
xrandr --output LVDS --left-of CRT1
```...make the script executable and reference the script in the autostart.

I tried both of those and they didn't work. I am a little rusty on scripts so I'll explain what I did to make sure I got it right:

1. opened leafpad, copied code you posted, saved (when hovering over file with mouse it said it was a shell script)
2. right clicked, properties, made it run as program
3. referenced the code directly in the startup by browsing, so no chance I mistyped it.
4. restarted and monitors were back to mirrored. typed the code into terminal and they were corrected?

Any more ideas why this won't work? or did I just mess up the script?

---

### Post by Toz on 2012-08-12
Can you post the exact contents of your script?

Also, have a look at ~/.xsession-errors (a hidden file in your home directory) to see if there are any error messages about xrandr in it.

You could also try setting up the dual monitors through lightdm configuration. To do so, edit (as root) the file /etc/lightdm/lightdm.conf (from a terminal window):
```
sudo cp ~/xrandr_setup /usr/local/bin
gksu leafpad /etc/lightdm/lightdm.conf
```
...and add the following line to the end of the file:
```
display-setup-script=/usr/local/bin/xrandr_setup
```

---

### Post by LLCoolJeff on 2012-08-12
> **Toz said:**
> Can you post the exact contents of your script?

Also, have a look at ~/.xsession-errors (a hidden file in your home directory) to see if there are any error messages about xrandr in it.

You could also try setting up the dual monitors through lightdm configuration. To do so, edit (as root) the file /etc/lightdm/lightdm.conf (from a terminal window):
```
sudo cp ~/xrandr_setup /usr/local/bin
gksu leafpad /etc/lightdm/lightdm.conf
```...and add the following line to the end of the file:
```
display-setup-script=/usr/local/bin/xrandr_setup
```

went to my home folder and checked view>show hidden files and nothing came up

also did command ls -a and got this:

```
jeff@Steez:/home$ ls -a
.  ..  jeff  lost+found

```

Thanks for your reply, I don't have the will to try the second part of your post right now, its beaten me down too much. I'll come back after some sleep and try it

---

### Post by LLCoolJeff on 2012-08-12
Ok I found the .xsession-errors. I was looking in the directory /home, not my "home" directory, sorry for the mixup.

Anyway there is no mention of xrandr in there...

---

### Post by erind on 2012-08-12
> **LLCoolJeff said:**
> I recently did a clean install of xubuntu 12.04 and set up dual monitors, I had to run 
```
xrandr --output LVDS --left-of CRT1
```to get the monitors to display side by side correctly, and the tutorial I was reading said it will undo itself upon logout so I should add it to the "session and startup" commands.

I made a command that looked like this:

[...]

but the next time I logged out and logged back in, the monitors had reverted to the way they were before. I went back into where I typed the command and copied and pasted it into the terminal and it worked great, so why did it not run the command and work when I logged in?

THanks


That's because the *X display*  wasn't fully up when your *xrandr* command was run. So give it sometime for **X** to start up **completely** with the* sleep* command, then run *xrandr* :

```
sleep **5** && xrandr --output LVDS --left-of CRT1
```Change sleep's value **5** to a different one if needed. As suggested you can use a script too:

*xrandr_setup*

```
#!/bin/bash
sleep 5 && xrandr --output LVDS --left-of CRT1
```I don't have a dual setup momentarily, but I tested with the code below, and it worked fine.

```
sleep 5 && xrandr -s 1400x1050
```

---

### Post by LLCoolJeff on 2012-08-12
> **erind said:**
> That's because the *X display*  wasn't fully up when your *xrandr* command was run. So give it sometime for **X** to start up **completely** with the* sleep* command, then run *xrandr* :

```
sleep **5** && xrandr --output LVDS --left-of CRT1
```Change sleep's value **5** to a different one if needed. As suggested you can use a script too:

*xrandr_setup*

```
#!/bin/bash
sleep 5 && xrandr --output LVDS --left-of CRT1
```I don't have a dual setup momentarily, but I tested with the code below, and it worked fine.

```
sleep 5 && xrandr -s 1400x1050
```

this worked beautifully sir, thank you!! :) My computer did freeze a minute or two afterwards though. complete complete screen lockup with the mouse stuck on the "hand".

But I'm not sure if its related so I'll make another thread for this:

[http://ubuntuforums.org/showthread.php?t=2041547](http://ubuntuforums.org/showthread.php?t=2041547)

---

### Post by sienile on 2012-08-12
You should mark this as solved so others can find this solution easier.

---

