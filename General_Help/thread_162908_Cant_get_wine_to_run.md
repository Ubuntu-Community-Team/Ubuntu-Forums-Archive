---
title: "Cant get wine to run"
date: 2006-04-19
forum: General Help
---

### Post by Muag on 2006-04-19
Ok, I downloaded and installed wine and now im not for shure how to get it to run...please help!!!

---

### Post by akiro.yamamoto on 2006-04-19
Usually after wine is installed you will need to run 
```
winecfg
``` to configure the wine application layer.
after that just double click (run) the win app you want to install.
You can check the winehq.com application database for a list of currently supported apps and configuration info.
You can also try a trial version of Codeweaver which helps you set-up your win apps.
Hope this info helps. ;)

---

### Post by Muag on 2006-04-19
yeah, that helps abunch...thanks

---

### Post by Mishal on 2006-04-19
Once the Crossover Office trial period finishes, does the software installed by Crossover also stop functioning?

Also, when wine asks to install a Windows software in a directory do I choose? C:/Windows/Program Files? But what if I already have that software installed in Windows?

Thanks :)

---

### Post by Mishal on 2006-04-20
Bump!

---

### Post by DoktorSeven on 2006-04-20
Once the Crossover engine expires you can't use it to run its installed applications.  It might be possible to use other wine programs to run stuff installed by it.

And you can install it anywhere you want; the default is usually c:\Program Files\programname, where C: is a "fake" drive under ~/.wine/drive_c/ by default.  If you have it installed in Windows it might be possible to run it from its installed location on a mounted Windows drive for *some* programs -- others might require an actual install under the "fake" C drive.

---

### Post by Charax on 2006-04-20
I too have Wine-related problems. Every time I install it and try to run a windows .exe, I get the message below.

I tried using winecfg to see if I could alter where it stores temp files, but I can't.

---

### Post by oberoc on 2006-04-20
I haven't personally used wine, but here is something I found in the magic google box: [http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys). I think that might be somewhere to begin.

-Tino

---

