---
title: "state of external monitor support"
date: 2010-01-13
forum: General Help
---

### Post by hunteke on 2010-01-13
My experience with external monitors in Linux is harrying at best. It's getting better, but it still ain't perfect. My current experience (I have an nVidia card, with nVidia drivers, on a Vostro laptop):

[LIST=1]
[*] Turn on computer (booting Karmic).
[*] Connect external monitor
[*] Click on System->Preferences->Display
[*] Redirect to nVidia's tool
[*] Perform at least 8 more clicks to enable secondary monitor.
[*] Realize resolution isn't optimal and set it with another few clicks.
[*] Click Apply
[*] Accept changes
[*] Quit, then really quit, the app.
[/LIST]

Notes:
[LIST]
[*]I always have to set the resolution, it doesn't detect it automatically.
[*]The main screen is *always* on the external monitor no matter my settings.
[*]I'm screwed if I unplug the monitor but forget to go through steps 1-8, this time disabling the external monitor. I have to replug it in, then turn it off, then I can unplug it.
[*]If I unplug the external monitor and plug in another one (going through steps 1-8 twice more) with different resolution capabilities (e.g. a projector), the settings get all messed up again.
[/LIST]

Why can't adding an external monitor be automatic?  It nearly is on OS X for instance.  I plug it in, and it automatically detects the monitor and makes it a secondary monitor, or mirrors them, or turns it on and turns off the laptop screen.  All the while being consistent about it.  When I unplug the monitor, it knows instantly that I've done that, and reconfigures the laptop screen once again.

I imagine the answer is because no one has stepped up to do it yet, or it's in progress. So my question: what *is* the state of external monitor codes in Linux, and are there any plans to implement them in Lucid? Further, what would be a project, with *user friendly* context, to which I could tune in?

Or, am I not aware of the "right way" to do it?

* I define user friendly as roughly the level of kernelnewbies.org .  That is, kn.org is my gauge of what I can understand.

---

### Post by Darce on 2010-01-13
LOL, I know where your coming from and can reduce the number of steps you take by one.

Open the NVIDIA X Server Settings. Click on 'nvidia-settings configuration' and de-select 'Show "Really Quit?" Dialog'

I often hook my laptop up to a plasma for wathing movies and go through a similar procedure to yours, although my resolution settings auto detect. I set my displays as clones and run into trouble when I switch them back and disconnect the plasma. On my laptop screen, when I maximise and window or app, it only fills up 3/4 of the screen. A restart fixes the problem, not ideal, but it works   ;)

Cheers,

Tim

---

