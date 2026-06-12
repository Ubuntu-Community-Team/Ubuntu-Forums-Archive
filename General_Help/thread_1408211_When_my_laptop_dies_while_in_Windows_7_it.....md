---
title: "When my laptop dies while in Windows 7 it...."
date: 2010-02-16
forum: General Help
---

### Post by Jackzor on 2010-02-16
Saves everything I was doing somewhere and then reloads it when ever I boot back into it. This includes when I power my computer and boot to ubuntu. I want Ubuntu to do the same thing. Its just like closing a VM and picking save state. How would I go about doing this?

---

### Post by 3rdalbum on 2010-02-16
It's called Hibernation. Go to the top-right corner of the screen and click on your name. Go down to Hibernate.

I believe you can specify to Gnome Power Manager that you want to hibernate when the battery gets low - try right-clicking on the battery icon in your notification area and choosing Power Settings (or something like that).

---

### Post by Jackzor on 2010-02-16
So if I do that my computer will instead of just.. going dead, I will be able to boot back to ubuntu later and ALL of my windows and programs will still be running even if, lets say, I took the battery out (after it died)

---

### Post by 3rdalbum on 2010-02-16
> **Jackzor said:**
> So if I do that my computer will instead of just.. going dead, I will be able to boot back to ubuntu later and ALL of my windows and programs will still be running even if, lets say, I took the battery out (after it died)

Exactly. Hibernation saves the contents of RAM to your hard disk, so it doesn't depend on your machine continually having power.

Hibernation only works if you have more swap than RAM - for instance, if you have 2 GiB of RAM in your machine, you must have a swap partition of 2 GiB or more.

---

### Post by Jackzor on 2010-02-16
Okay. Well How do I make it do that right before it dies? At like 2% left?

---

### Post by dixie460 on 2010-02-16
As mentioned above, you need to specify that in your power management settings. I don't have my laptop with me right now so I can't take a look, but just poke around until you find something that asks what to do when the battery reaches a critically low state. I know I have mine set to hibernate, when my battery gets low I get a message saying the system will hibernate in such amount of time, and when I let it die and then power back on, everything is as I left it. Even Audacious 2 is still jammin :p

---

