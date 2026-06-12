---
title: "Run command at startup"
date: 2010-09-15
forum: General Help
---

### Post by anberside on 2010-09-15
I've searched everywhere in the forums. Although, i can't find a solution that works. i have a file, 2fsrl, that i want to run at startup. If i type /home/kent/2fsrl in the terminal it works. Although it won't work if i put the command in Startup Applications. 

In my file is this:
synclient VertTwoFingerScroll=1
synclient HorizTwoFingerScroll=1
synclient EmulateTwoFingerMinW=5
synclient EmulateTwoFingerMinZ=48

It's for 2 finger scrolling

---

### Post by eric_1982 on 2010-09-16
have you tried to the files permission to make it executable?

You could also try adding it to rc.local.

---

### Post by MooPi on 2010-09-16
If the app runs in terminal it will need that instruction in the startup. Something like this ```
gnome-terminal -e your_application
``` I use Openbox and I have used in the past a start up ```
xterm -e htop
```

---

### Post by anberside on 2010-09-19
ah thank you Moopi! That did the trick. Thanks a ton!!

---

