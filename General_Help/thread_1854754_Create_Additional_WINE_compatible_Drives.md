---
title: "Create Additional WINE compatible Drives???"
date: 2011-10-05
forum: General Help
---

### Post by screamthepoetry on 2011-10-05
hi i was wondering if anyone knew how to create another WINE compatible drive? what i mean is the standard WINE setup is on the same partition as my Ubuntu Set up, i only used a 40gb Sata drive to as my File system and just use seperate Bigger sata drives for installing stuff and storage. I am running an install using WINE but i dont have enough space on that drive to install it. So i was wondering if anyone else has been able to create a seperate wine setup on another drive?

---

### Post by Toz on 2011-10-12
Hello and welcome to the forums.

The ~/.wine directory (assuming you are using the default wine setup) is a self-contained environment. You can move it to the other drive as a whole.
```
mv ~/.wine /mnt/other/drive
```

Then you can either use WINEPREFIX ([http://wiki.jswindle.com/index.php/Wine_Prefixes]("http://wiki.jswindle.com/index.php/Wine_Prefixes")) to point to this new location or create a link between ~/.wine (the expected location) and /other/drive/.wine (the new location). 
```
ln -s /mnt/other/drive/.wine ~/.wine
```

Are you using any particular wine front-end (PlayOnLinux, Crossover Office/Impersonator, etc)?

---

