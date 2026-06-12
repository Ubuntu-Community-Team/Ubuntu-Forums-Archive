---
title: "how to disable defect hardware?"
date: 2006-06-12
forum: General Help
---

### Post by Peturrr on 2006-06-12
**The Problem**
Since yesterday I have the old laptop of my dad. It's a celeron 1 ghz, so it's still very usable for me. The reason he replaced it, was because of the strange errors that the mouse en keyboard gave.

I have found out that there is some kind of electricity leak that influences the keyboard and mouse. While not pressing any key or moving the mouse I get errors like: 
```
localhost kernel: [ 1634.549478] atkbd.c: Unknown key pressed (translated set 2, code 0x0 on isa0060/serio0).
```

I have now attached an external keyboard and mouse and don't have problems with them. The only problem is that the laptopkeyboard and mousepad still give errors and 'take over' my typing with erronous keys.

**The Question**
I would like to disable the original keyboard and mouse so the system won't respond to any commands invoked on their behalf. How would I do that? It needs to be on kernel level, but to disable it in X would also be very nice.

So, how would I disable isa0060/serio0 ?

---

### Post by traveller.ct on 2006-06-12
You could try commenting out the [FONT=Courier New]InputDevice[FONT=Verdana] of your faulty keyboard and mouse in [FONT=Courier New]Section "ServerLayout"[FONT=Verdana] in[/FONT][/FONT] [FONT=Courier New]/etc/X11/xorg.conf[FONT=Verdana].[/FONT][/FONT][/FONT][/FONT]

---

### Post by Rui Pais on 2006-06-12
hi,
the question is if your new keyboard and mouse use the same modules/drivers or not. 
If they use the same you can't prevent them to load or the new hardware will stop working with old ones...

If not, then if you know which modules old mouse and keyborad uses you can try to prevent it to load. Maybe add them to /etc/modprobe.d/blacklist is enough... Or eventually if they are build in the kernel you have to rebuild the kernel without those or build them as loadable modules.
The hard part is that ususally mouse and keyboard have very generalist modules and they have to be load for a lot of keyboard/mouses work...

sorry, i know that this is not an answer for your question, just some suggestions...

good luck

---

