---
title: "No window dressing, can't change windows"
date: 2011-09-15
forum: General Help
---

### Post by tomkat3 on 2011-09-15
So this is frustrating.

I just booted into Xubuntu 11.04, and suddenly there's all these problems with the window manager.

1. No windows have title bars. There's nothing to grab that allows me to resize the window. Its a bit strange: I when I opened Firefox, the window wasn't maximised and glued to the upper left corner of my screen. Instead of the upper tool bar with the little xfce logo and a list of open windows, I just saw "File   Edit   View   History" sort of like a mac.

2. I can't switch windows using Alt+Tab, close with Alt+F4, or any other window hot keys. I first opened Firefox, then when I noticed the window was screwed up, I opened a terminal to find what I did when this happened in my old Ubuntu 10.04 with Gnome.

3. I had the 2 default workspaces, but this glitch appears to have taken that away as well. I only have one now, and nothing happens when I change the settings in the Settings Manager.

4. Just as a thought, I went to the Window Manager section of the settings manager to see if I could uncheck the "break everything" box, but the window manager section was totally blank! Nothing to change!

I can't think of anything I could have done to mess it up this badly. The only thing that comes to mind is that I recently installed Ubuntu Tweak and changed the background of the login screen. I can still browse the web, but I can only use the last application I've opened since I can't switch windows.

Its this sort of instability that keeps Microsoft in business...*grumble grumble*

---

### Post by sanderd17 on 2011-09-15
certainly the windows borders makes me think of a compiz problem.

Can you see if you have compiz installed? You should not need it on Xubuntu.

---

### Post by tomkat3 on 2011-09-15
Yep, I did install compiz. But I think I installed it a week ago. Why do these things wait until you've forgotten about them to act up?? I just removed it...

Also, I was able to go back to normal in a strange way. I opened a terminal and typed:

```
xfwm4
```

The screen sort of flickered to my desktop background. Then things got closer to normal, except the title bars were missing. The terminal wouldn't take more inputs, like it was running a program. 

I wanted to add more inputs to the xfwm4 command to get all the way back to normal, so I hit Ctrl  + C to cancel. The screen flickered back to my background again, and then everything was normal!! wtfff?

Does this mean xfwm was never running? Any idea what just happened and why my random command fixed it?

---

### Post by sanderd17 on 2011-09-15
yes, that means that compiz had taken it over from xfwm. And compiz can do weird things.

---

### Post by tomkat3 on 2011-09-15
Ok, I had to reboot for unrelated reasons and it happened again, and again I fixed it by typing in xfwm4 and cancelling the process with ctrl+C. Is there a way I can tell it to do that every time or permanently fix whatever compiz messed up? Again, I've removed compiz so nothing new should be getting in the way...

---

### Post by vangelas on 2011-09-15
I had a similar problem on ubuntu and it was fixed by disabling extra visual effects. I think it had something to do with the graphics card AND compiz.

---

### Post by sanderd17 on 2011-09-16
> **tomkat3 said:**
> Ok, I had to reboot for unrelated reasons and it happened again, and again I fixed it by typing in xfwm4 and cancelling the process with ctrl+C. Is there a way I can tell it to do that every time or permanently fix whatever compiz messed up? Again, I've removed compiz so nothing new should be getting in the way...

Starting xfwm4 is no problem, but killing it can be a problem.

Can you see if there is another command that does the work? Something like "xfwm4 --restart" or so. Or try a combo of two commands like

```

xfwm4 &
killall xfwm4

```

If you find such terminal-only solution, you can put it in the file .local in your home directory. That file is executed at login. If the file .local doesn't exist, create it.

If it does not work immediatly with the .local script, maybe you will need to add a sleep (to wait before xfce is completely loaded). But I'll hear from you if it works or not.

---

### Post by tomkat3 on 2011-09-16
Thanks for the help! It seems to have fixed itself after I shut down and did something else for a few hours.

---

