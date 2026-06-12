---
title: "HP printer working, no device found?"
date: 2006-04-18
forum: General Help
---

### Post by Joey French on 2006-04-18
Hi all,
I am using a HP Deskjet 5650 under Breezy, works fine, no problems printing. The problem is, according to the [ubuntu wiki]("https://wiki.ubuntu.com/HpPrinterInstallationAndMaintenanceBreezy"), I should be able to run

```
hp-toolbox
hp-clean
hp-align
hp-levels
```

however, when I do, I get this...

```
joey@homebox:~$ hp-clean

 HP Linux Imaging and Printing System (ver. 0.9.5)
 Printer Cartridge Cleaning Utility ver. 1.5

 Copyright (c) 2003-5 Hewlett-Packard Development Company, LP
 This software comes with ABSOLUTELY NO WARRANTY.
 This is free software, and you are welcome to distribute it
 under certain conditions. See COPYING file for more details.

 [ERROR]: No devices found.
 [ERROR]: Error occured during interactive mode. Exiting.
joey@homebox:~$

```

I think I am using the hplips driver, but under the KDE system > printer dialog, it says CUPS? Anyone know how to proceed? Should I just try reinstalling the printer? It works well, no problems, but it is low on ink and needs a head cleaning.

Thanks,
Joey French

---

### Post by Joey French on 2006-04-18
I should maybe add this is connected via LPT, not usb, if that makes any difference at all. Can anyone think of something to try?

---

### Post by uteck on 2006-04-18
Perhaps it needs to run as root?

---

### Post by Joey French on 2006-04-18
Nope. What's the best way to reinstall the hpips driver? Should I just reinstall the printer?:confused:

---

### Post by uteck on 2006-04-19
[QUOTE=Joey French]Nope. What's the best way to reinstall the hpips driver? Should I just reinstall the printer?:confused:[/QUOTE]
dpkg-reconfigure hpijs

Also, the latest version is 0.9.10  You can grab the source from [http://hplip.sourceforge.net/](http://hplip.sourceforge.net/) and compile it ar try using the version from Dapper, but I don't know what version it is using.

I just found a bug report for 0.9.7 that says this bug was fixed.  So you need to upgrade to use this feature.

---

### Post by Joey French on 2006-04-19
Okay, I compiled the newest from SourceForge, 0.9.10, but when I make install it runs for a bit, then complains and exits...
```
/bin/sh: hplip: command not found
make[3]: *** [install-data-hook] Error 127
make[3]: Leaving directory `/home/joey/hplip-0.9.10'
make[2]: *** [install-data-am] Error 2
make[2]: Leaving directory `/home/joey/hplip-0.9.10'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/joey/hplip-0.9.10'
make: *** [install-recursive] Error 1
```

Now what? I have tried all from 0.9.7 to newest, they all complain about the same thing. Not sure how to proceed. It would make my day to get this handled, as it seems to be one of very few things my girlfriend complains about.

---

### Post by Joey French on 2006-04-19
Aslo, I see now that my KDE toolbar has an "HP LIPS Toolbox" icon, but when i click it, it does nothing.:(

---

### Post by Joey French on 2006-04-20
I get no result from 'dpkg-reconfigure hpijs', either. It just hangs there, until I exit the terminal.

---

### Post by Joey French on 2006-04-29
Bump...?

---

### Post by Joey French on 2006-06-11
Solution: Upgrade to dapper, hp-toolbox works no problem.

---

### Post by earlycj5 on 2006-06-11
Dapper hp-toolbox doesn't work for me...

---

### Post by Joey French on 2006-06-11
In synaptic, look for "hplip", install. Remove your current printer profile using your DE configuration tool (in KDE, System Settings > Printers).  Then, go to [http://localhost:631/](http://localhost:631/), add your printer there, then call hp-toolbox. 

For some reason, I had to reinstall the printer before it was recognized. This only took like two seconds though, and now hp-toolbox works swimmingly.

---

