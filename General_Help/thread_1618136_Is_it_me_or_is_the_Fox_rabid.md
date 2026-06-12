---
title: "Is it me or is the Fox rabid?"
date: 2010-11-10
forum: General Help
---

### Post by Boosh007 on 2010-11-10
I downloaded the 10.10 desktop version. Everything seems to work fine except Firefox. Sure, I can get on, but getting out is something of a chore. Half the time the page freezes and won't allow me to try anything else. I tried; Clicking on the red "X" = nothing
                    Right-clicking on the page and selecting "Back" = nothing
                    Right-clicking on the task bar and selecting "Close" = nothing
                    Restarting the computer = nothing

The only way to get out when that happens, is to hold down the "Power" button. I know it's not good for the computer, but being held hostage in Firefox is not good for my patience (lol). Even that is a crap-shoot. Sometimes it boots back up fine, only to resume what happened before the power went out when I log back into Firefox. Sometimes it won't let me out until I scan back to the main page by using the arrows one page at a time...This kind of thing never happened when I had the 9.04...Any ideas?...

---

### Post by 3Miro on 2010-11-10
If a single program goes rogue, you can go to System -> Admin -> System Monitor and kill it from there. You don't have to reboot everything.

Another thing that you can try to figure out what is happening with FF is to run it from a terminal (Apps -> Access -> Terminal). Then you can start it with "firefox" and look for the last error messaged before it crashes.

---

### Post by WorMzy on 2010-11-10
I think it's just you, I'm afraid. Have your tried using another browser, such as Chromium, Opera, Midori, etc? 

Next time it happens, switch to a virtual terminal (if possible) by pressing Ctrl+Alt+F1. Log into it and run "top", and see whether any process is using 100% CPU. I'm guessing you have an old P4 processor or equivalent, with a single core?

Press "q" to exit top, and then kill firefox with
```
killall -9 firefox
```

Switch back to your graphical desktop by pressing Alt+F7.

---

### Post by mister_playboy on 2010-11-10
> **Boosh007 said:**
> I downloaded the 10.10 desktop version. Everything seems to work fine except Firefox. Sure, I can get on, but getting out is something of a chore. Half the time the page freezes and won't allow me to try anything else. I tried; Clicking on the red "X" = nothing
                    Right-clicking on the page and selecting "Back" = nothing
                    Right-clicking on the task bar and selecting "Close" = nothing
                    Restarting the computer = nothing

Sounds like a Flash problem... does this happen on specific sites like YouTube?

---

