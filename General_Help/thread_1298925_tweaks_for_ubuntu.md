---
title: "tweaks for ubuntu"
date: 2009-10-23
forum: General Help
---

### Post by starcraftmaster on 2009-10-23
Ubuntu 9.04

hey guys
i got a old computer
and ubuntu runs ok/notbad

i remember that it used to run more better

so am guessing i turned some thing on or off which has made the computer run slow

so any one know any good tweaks that don't do much(as in don't take visual graphics away or take away good things)

---

### Post by Giblet5 on 2009-10-23
Please be more specific. A PC's performance can appear to change dramatically just by drinking a cup of strong coffee.

What slowed down? If you say "everything", then you can fix this by laying off the coffee for the rest of the day. ;)

What does System Monitor think is going on? (System menu -> Administration -> System Monitor)

---

### Post by starcraftmaster on 2009-10-23
theres a lot of processes
but 200 mb is  being filled up
i got 512mb of ram
and cpu power left alone is around 1-7%


i heard that making the swap smaller can make the system faster
i got no idea how that would make things faster
but should i give that a go ?(the swap hardly gets used any way so it don't matter if i make it smaller)

---

### Post by Lukios on 2009-10-23
Making the swap smaller will make the computer less likely to use swap instead of ram. Swap is way slower then ram and when it is used to run your programs there will be a significant drop in performance. Ubuntu in general, whether it be xubuntu or ubuntu, is bloated. I'm afraid that this will probably be true with Lubuntu considering the nature of Ubuntu in general. In any case, one sure way of having a faster Ubuntu install is to install from the Mini.iso and only installing the bare essentials. For example, instead of installing the gnome-desktop that comes with Ubuntu, you can install gnome-core which will only give you what you need. You can then build from there. If you don't want to go that rout, you can always replace nautilus and metacity with pcmanfm and openbox.

You can always look in your startup programs and see what is running that is not needed. You can also adjust your update manager to only look for updates every day instead of ever 5 minutes. There are lots of things you can do, just google it.

---

### Post by dhughes on 2009-10-23
> **starcraftmaster said:**
> Ubuntu 9.04

hey guys
i got a old computer
and ubuntu runs ok/notbad

i remember that it used to run more better

so am guessing i turned some thing on or off which has made the computer run slow

so any one know any good tweaks that don't do much(as in don't take visual graphics away or take away good things)

 Well there's the problem, you have an old computer and probably have 'extra' visual effects selected. You said it used to run better but now it isn't, did you always have the visual effects at the setting they are set at now? I'd say dial down the visual effects to 'none' and try it from there.

 Check processes using 'top' (command line) or 'system monitor' (gui) to see what process are causing your system to slow down. The usual culprits are Java and any search or indexing apps such as beagle, tracker etc. or any torrents apps, I know Transmission a torrent app would use enormous amounts of memory when left on for days or weeks when I used it.

---

### Post by starcraftmaster on 2009-10-24
well i dont want to replace ubuntus main programs
also i try it for a day with out any visual effects ok



one more thing:
[http://upload.wikimedia.org/wikipedia/commons/e/ec/Metacity-screenshot.png](http://upload.wikimedia.org/wikipedia/commons/e/ec/Metacity-screenshot.png)

how can i get that cool hard drive icon

---

### Post by starcraftmaster on 2009-10-24
well
ubuntu seems to run petty good

its just browsing
sorry for the mistake


any way
i remember that firefox and opera used to run so much better
now they run slowly and sluggish


guessing a java problem ?

---

### Post by Lukios on 2009-10-25
another thing that may help is installing preload

---

