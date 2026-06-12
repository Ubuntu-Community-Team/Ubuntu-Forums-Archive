---
title: "having huge problem, need fix quick!"
date: 2010-08-20
forum: General Help
---

### Post by jp351 on 2010-08-20
ok.. my issue started with trying to play 2 or 3 games on my system, running 9.10, and during one of these games, i'd get a "microsoft c++ runtime error".. using the terminal, i launched winetricks.. "sh winetricks".. then proceeded to install a couple of the microsoft c++ libraries, namely the 2005 express, after running the "ver=" i believe it was, for setting the version to win xp, which i know these games run on. anyway, i accidentally installed the "ms c++ 2005 express sp1", which it says "(does not yet work)".......... now my computer is a little unresponsive, taking a WHILE to launch certain things.. my MAIN concern is that now i can't even launch winetricks... and i don't know how to remove sp1..

i need help.. PLEASE!!!!!!!!!!

*EDIT*

well, now after trying to run a few apps, i see that it's not that no ".exe" files run, but even trying to uninstall a program, i might get a c++ runtime error (again, probably because of having accidentally installed the sp1 with winetricks) but it will take a good 3 mins before the unistaller (or whatever) will launch.. more or less, it's anything i do with wine itself that's unresponsive and slow..

---

### Post by joshedmonds on 2010-08-21
Firstly, I don't know how you would uninstall something installed with winetricks.

The best way to avoid borking your entire Wine catalogue is to use a dedicated WINEPREFIX for each application. This will ensure any issues are confined to that WINEPREFIX and won't affect other programs. Using a separate WINEPREFIX is somewhat analogous to running each program in its own VM (although Wine is not an emulator).

In this case I would rename the ~/.wine directory to ~/.wine-old , and start fresh with each program in its own prefix. You should be able to copy settings (savegames etc.) for each program from the .wine-old folder into the new prefixes.

Basic usage of WINEPREFIX:
```
$wineconfig # to create a new ~/.wine directory
$mkdir ~/.wine/NEWFOLDER/ # create directory for each application under ~/.wine
$export WINEPREFIX=$HOME/.wine/NEWFOLDER # tell Wine to use that WINEPREFIX
$wineconfig # prepare NEWFOLDER as a WINEPREFIX
```

Run wine as before. The current WINEPREFIX (folder) will be used instead of ~/.wine. Wine will correctly handle shortcuts etc. but to use Wine (or winetricks etc.) with a particular WINEPREFIX in future simply:
```
$export WINEPREFIX=$HOME/.wine/NEWFOLDER
```

Further reading:
[http://wiki.jswindle.com/index.php/Wine_Prefixes]("http://wiki.jswindle.com/index.php/Wine_Prefixes")
[http://www.thelupine.com/content/wine-and-wineprefix-variable]("http://www.thelupine.com/content/wine-and-wineprefix-variable")
[http://wiki.winehq.org/FAQ#head-faf9617c53607e583f6e6ff70a4ac9522d490faf]("http://wiki.winehq.org/FAQ#head-faf9617c53607e583f6e6ff70a4ac9522d490faf")

---

### Post by jp351 on 2010-08-21
thanks for the info. i'm looking into different ways i can manipulate wine and winetricks for that kind of thing.... but after i did a little "light" reading on the winetricks site, which yeah i should have done first, it's clearly stated

"uninstalling what's been installed via winetricks:
yeah, it's not gonna happen"
..pretty much..

but again, thanks for the info. right now i'm just trying to remove the 2005 c++ sp1 whatever that i did install. like i said before, it wasn't until i ran that one that i started having problems.

*edit*
i don't know if going through all that will fix it though.. i installed a package via winetricks, so it's just a matter of figuring out what it did with the package, where it was place/installed, etc..... if that's even possible..

---

### Post by joshedmonds on 2010-08-21
> **jp351 said:**
> it's clearly stated
"uninstalling what's been installed via winetricks:
yeah, it's not gonna happen"
...
i don't know if going through all that will fix it though.. i installed a package via winetricks, so it's just a matter of figuring out what it did with the package, where it was place/installed, etc..... if that's even possible..
That was my concern. Considering how many people use (and rely on) winetricks, it is a bit of a black box.

---

### Post by jp351 on 2010-08-21
> **joshedmonds said:**
> That was my concern. Considering how many people use (and rely on) winetricks, it is a bit of a black box.
i think "black box" is a bit of an under statement... doing something like i did,not paying attention and clicking the wrong dam checkbox, u'll open pandora's box... :/

---

