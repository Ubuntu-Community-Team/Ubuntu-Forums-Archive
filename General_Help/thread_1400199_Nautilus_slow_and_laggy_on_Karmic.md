---
title: "Nautilus slow and laggy on Karmic"
date: 2010-02-06
forum: General Help
---

### Post by mac666 on 2010-02-06
Hey
Im experiencing Nautilus slow and laggy.
By slow i mean that navigating between localdrives / filesystem folders can load for some seconds (1-3 sec), but it should be immedate? The folders can be empety or filled with stuff, doesnt matter. 
Like using back button to go back to and empty folder can take about 1,8 sec.


By laggy i mean that it can freeze when i rightclick small / big files, but this doesnt accour at all times. How ever the slowness is allways there...

Any ideas? Any that feel the same?

Computer setup is a intel quad, 4x ddr3, sata 7.2k rpm.
Nothing that should lag it up?

---

### Post by Ziggy72 on 2010-02-06
I haven't heard of that problem, but there are some issues with nautilus in Karmic. If you close down all instances of nautilus and then, in a terminal, type "nautilus" (no quotes) do you get any error message before nautilus appears... e.g. eel-CRITICAL **......? If so, I can probably help. If not, I'm sorry but I have no suggestions.

---

### Post by mac666 on 2010-02-07
```
(nautilus:4045): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

```

Would you like to help me with that? :)

---

### Post by Ziggy72 on 2010-02-08
That nautilus error prevents the proper functioning of Nautilus Actions Configuration (among other things). I doubt if it contributes to your problem - but who knows?

To correct it, add the following to your /etc/apt/sources.list:
```

deb http://ppa.launchpad.net/erez-volk/nautilus/ubuntu karmic main 
deb-src http://ppa.launchpad.net/erez-volk/nautilus/ubuntu karmic main 

```
Then, in a terminal:
```

apt-get update
apt-get upgrade

```

That will eliminate the 'Eel-CRITICAL...' error. Let us know if it affects your 'laggy' problem.

---

