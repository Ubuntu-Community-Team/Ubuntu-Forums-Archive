---
title: "corrupted ubuntu 11.0.4 desktop"
date: 2011-09-30
forum: General Help
---

### Post by froghunter302 on 2011-09-30
Hello i am having trouble solving this problem, i am trying to set this computer up for the kids to play on, it is nothing special, just an old dell dimension 3000, it was designed to run xp but that is not the most kid friendly os.
so far i have logged off and switched to classic view with no graphics, the image is still corrupt but not as bad. before you could not even see the time vpn menu the power button or any of the top left. and if you clicked where they were they would pop up and dissipater in a split second. now they at least stay up.

here is a screen shot of what is going on. i would really appreciate any help!

---

### Post by seawolf167 on 2011-09-30
You can try and see if any available graphics drivers for your system helps at all - go to System -> Administration -> Hardware Drivers (and check for graphics drivers to install)

---

### Post by froghunter302 on 2011-09-30
> **seawolf167 said:**
> You can try and see if any available graphics drivers for your system helps at all - go to System -> Administration -> Hardware Drivers (and check for graphics drivers to install)
just tied that i could not do it exactly because there was no hardware tab so instead clicked "additional drivers" it scanned and said none were available.

i was looking on other forums and i someone said to run command "killall gnome-panel"
i tried to run that in terminal bit it said there was no such command, i tried it again putting "sudo" in front of it with no luck.

i relay appreciate your time in replying, thanks a lot seawolf!

---

### Post by seawolf167 on 2011-09-30
Aye - I forgot they change the name, its the same thing.

Try this to reset the panels to their defaults:

Enter the commands in a terminal (Applications -> Accessories -> Terminal), it'd probably be easier to copy/paste them.

```
gconftool-2 &#8211; -shutdown
gconftool &#8211; -recursive-unset /apps/panel 
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

