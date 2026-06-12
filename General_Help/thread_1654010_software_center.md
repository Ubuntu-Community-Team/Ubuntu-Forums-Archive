---
title: "software center"
date: 2010-12-27
forum: General Help
---

### Post by Trogladyte on 2010-12-27
Greetings earthlings

Treat me gently - I am very new to Ubuntu, but reasonably familiar with the concepts of Windows and DOS and GUIs and command line interfaces n stuff.

Anyway, a Windows laptop my son was using died ( I think the HDD may have cooked and got lots of bad sectors, rendering the recovery partition unusable). So I reformatted it and loaded Ubuntu 10.10. This worked beautifully for a couple of days, but I was getting the (i think common) Modprobe error on boot. So I took some advice from a forum, and reinstalled. Since then I have had a few problems...

The modprobe error has gone. But I keep losing Ubuntu software center - it starts loading from the GUI but then disappears before the window opens. Running it from a terminal results in an error. I also couldn't get int update manager. I ran a full update from a terminal and that restored Update Manager but not Software Center. So I uninstalled and reinstalled the software center with Synaptic, and it worked again. I used it to install the planetarium, which was cool until I opened it the second time and every time since - t just freezes on the opening screen, and guess what - yes, I have no Sofware Center again...

Anyone have any thoughts about what's causing this behaviour?

---

### Post by Trogladyte on 2010-12-28
OK. I'm not sure how you attract attention here - I'm drowning, not waving OK?

Here's the error from a terminal:

> Traceback (most recent call last):
  File "/usr/bin/software-center", line 88, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 43, in <module>
    from softwarecenter.view.widgets.mkit import floats_from_string
  File "/usr/share/software-center/softwarecenter/view/widgets/mkit.py", line 29, in <module>
    from mkit_themes import Color, ColorArray, ThemeRegistry
EOFError: EOF read where object expected
trog@trog-EasyNote-MZ36:~$ 


---

