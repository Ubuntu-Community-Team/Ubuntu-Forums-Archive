---
title: "getting the monitor to turn off"
date: 2009-08-15
forum: General Help
---

### Post by baracuda68 on 2009-08-15
Hi.
I use Ctrl+Alt+L a lot to lockout my desktop when I am AFK, but even though the LCD goes black,the back-light remains on...

I also know the command " xset dpms force off" to temporarily turn off the monitor, but this does not lock it out. Can I pipe the two functions together somehow?
:confused:  Thanks.

---

### Post by coldReactive on 2009-08-15
> **baracuda68 said:**
> Hi.
I use Ctrl+Alt+L a lot to lockout my desktop when I am AFK, but even though the LCD goes black,the back-light remains on...

I also know the command " xset dpms force off" to temporarily turn off the monitor, but this does not lock it out. Can I pipe the two functions together somehow?
:confused:  Thanks.

That's because when you lock the computer, it actually puts the screensaver on as well. You probably have "Blank Screen" set in your screensaver.

---

### Post by baracuda68 on 2009-08-15
> **coldReactive said:**
> That's because when you lock the computer, it actually puts the screensaver on as well. You probably have "Blank Screen" set in your screensaver.

Yes, this is true, I do have it set to "Blank Screen" which is what I wish it to be.
But how can I turn the backlight off while it is "blank"?

---

### Post by Horaci on 2010-06-22
I guess you found a solution already but just in case this helps anyone, I use the following script
> 
#!/bin/bash
sleep 0.5
xset dpms force off
gnome-screensaver-command -l


This turns monitor off and locks the session. The "sleep 0.5" is there to avoid the monitor turning on when you release the CTRL-ALT keys; maybe you don't need this.

hope this helps,

H

---

### Post by warfacegod on 2010-06-22
You could always *...push the power button on the Monitor?* Unless, of course, your using a laptop.

---

### Post by My 2 Cents Worth on 2010-07-01
The solution I use is:
#1 - I have added the Inhibit Applet to my top panel (this lets me toggle the sleep mode off and on)
#2 - In power management I set Put display to sleep when inactive for: 1 minute.
#3 - I use the Ctrl + Alt + L ( I actually changed my shortcut to Ctrl + Alt + Spacebar) to lock the screen.

So when I am using the laptop the first thing I do is click on my Inhibit Applet in my top panel so my display does not go to sleep in 1 minute of inactivity.

When I am all done and want to lock the screen and turn off the monitor I click on the Inhibit Applet so it allows the sleep timer to work, and I hit my combination of keys to lock the screen Ctrl + Alt + L.
The Screen is locked and in 1 minute the display turns itself off.

---

