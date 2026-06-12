---
title: "help with script for setting up external monitor"
date: 2011-09-08
forum: General Help
---

### Post by CryptKeeper777 on 2011-09-08
I have a second monitor I can plug into my Laptop which I from time to time use as extended workspace. It was quite hard to set up (see thread [here]("http://ubuntuforums.org/showthread.php?t=1821592")), but I finally managed it. But now, every time I want to set the second monitor up, I have to do a series of steps which I'd like to automatize with a script. The steps are the following:

- Settings > Settings Manager > Display > "Digital Display" (choose from list) > check "Use this output"
    --> now the monitor is activated, although still only in mirror modus
- command "xfwm4 --replace"
    --> I have to disable Compiz which GRandR doesn't like
- GRandR (command "grandr") > Layout > move "DVI1" from middle window to the right window
    --> monitor layout: the external monitor is to the right of the internal monitor
- command "compiz --replace"
    --> now that the monitor layout is set up, Compiz isn't a problem anymore, so I can reactivate it

The second and fourth steps are easy to put into a shell script, just insert the commands. The other two steps however are more difficult. I don't doubt that these steps are replaceable with command lines (GRandR is nothing else but a GUI for RandR, if I understand it right), but I don't know enough about these things. 

Can anyone with some experience with RandR and monitor setups help me out?

---

