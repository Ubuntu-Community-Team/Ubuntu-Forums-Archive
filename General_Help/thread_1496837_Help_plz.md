---
title: "Help plz"
date: 2010-05-29
forum: General Help
---

### Post by UnderPantGn0mes on 2010-05-29
uhhhhh u guys know the bottom bar on the screen????

yeah mines gone and idk how to get it back plx help me

---

### Post by UnderPantGn0mes on 2010-05-29
would be the GNOME pannel i guess

---

### Post by Dayofswords on 2010-05-29
the way i fix panel issues is reseting them to defualt by deleting the /home/USERNAME/.gconf/apps/panel folder, log out, log in

---

### Post by Autodave on 2010-05-29
> **UnderPantGn0mes said:**
> uhhhhh u guys know the bottom bar on the screen????

yeah mines gone and idk how to get it back plx help me

Open your teminal and type:  gnome-panel

---

### Post by UnderPantGn0mes on 2010-05-29
Cannot register the panel shell: there is already one running.


i know its the the window things cuz i was messing with that before this happend but now i still dont understand wuts going on xD i just want my GNOME Desktop back xD

---

### Post by wojox on 2010-05-29
Can't you right click the top panel and select New Panel?

---

### Post by UnderPantGn0mes on 2010-05-29
nothing happens when i do -_- and its not the pannels i want i want the gnome desktop back

---

### Post by UnderPantGn0mes on 2010-05-29
ahahahaha i found out -_- mee and my noobish ways of learning somthing completely new to me sy for the hassle to on every one

---

### Post by wojox on 2010-05-29
Try running these two commands:

```

gconftool --recursive-unset /apps/panel
pkill gnome-panel

```

---

### Post by UnderPantGn0mes on 2010-05-29
already figured it out and back to normal but im sure ill be back on the fourm in another topic here a bit xD getting used to somthing completly new and may mess up somthing here or there and need help :)

thx to all in advance :D

---

