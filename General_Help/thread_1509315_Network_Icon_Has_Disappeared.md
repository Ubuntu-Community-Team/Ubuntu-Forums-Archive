---
title: "Network Icon Has Disappeared"
date: 2010-06-14
forum: General Help
---

### Post by false_chicken on 2010-06-14
So I have done the most recent updates and I have noticed that my network icon, The one that sits in the try next to the volume control has vanished. I have tried removing and re-adding the items to the bar but that didnt help. And I know my hardware is fine as right now I have network and Internet access. Any advice?

---

### Post by Peter09 on 2010-06-14
Check in startup tasks that network manager is there and ticked.

---

### Post by philinux on 2010-06-14
> **false_chicken said:**
> So I have done the most recent updates and I have noticed that my network icon, The one that sits in the try next to the volume control has vanished. I have tried removing and re-adding the items to the bar but that didnt help. And I know my hardware is fine as right now I have network and Internet access. Any advice?

Is the rest of the notification area working i.e volume clock etc?

---

### Post by false_chicken on 2010-06-14
Yeah it is there and checked. And yeah everything else works. Does the network manager have a log I can look at?

---

### Post by false_chicken on 2010-06-16
This is a big issue because I cannot configure my wireless without it :(

---

### Post by philinux on 2010-06-21
Try resetting the panels to there default state.

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

You'll have to redo any panel customisation.

---

### Post by coldraven on 2010-06-21
Me too! This morning my network icon vanished and just left a black space!
It did connect by wifi though, strange.
After a reboot it's back, however it still has it's usual red exclamation mark for some unknown reason.
This is a fresh install of 10.04.

---

