---
title: "Ubuntu crashes after login"
date: 2010-02-09
forum: General Help
---

### Post by Brightneon_Latte on 2010-02-09
Hello:
I'm new to Ubuntu (Have tried it previosuly with hardy, but deleted it after a while). I have Karmik Koala (I downloaded and installed it yesterday).
I was applying effects with compiz manager and then, after selecting an effect called window or something like that (there's a picture of a window with some reflexion on it) my computer froze. I turned it off. turned it on again, got to the login screen, log-on, and after the introduction sound, the menu bar appeared a little bit dark and the ubuntu splash screen froze. I had no cursor on the screen, and the keyboard didn't responded. I have tried to log in 5 times, but it won't work. Is there any way I can restore the computer like it was before, or some way I can make the computer to run again??
Thanks

---

### Post by quixote on 2010-02-10
The command line way to turn off compiz is```
sudo metacity --replace
``` I assume that would also work in recovery mode, except then you don't need the "sudo" because you're already root.  To get out of recovery mode, I know you can type "halt now" (without quotes) to shutdown the machine.  I don't remember the more elegant methods to continue with the boot or to restart.  Either way, restart, and if compiz was the only problem, it should boot up normally.  

If it actually messed up your X (graphical interface) system, then we'll try to deal with that next.

---

### Post by flippo on 2010-02-11
If you don't have time to run metacity --replace before compiz freezes your machine try dropping to a terminal (ctrl+alt+f1 at login screen) removing or renaming the compiz configuration files (I think the .compiz directory in your home directory) then returning to the login screen (ctrl+alt+f7) and logging in.

---

