---
title: "Problems running/installing Amaya"
date: 2010-01-12
forum: General Help
---

### Post by akakingess on 2010-01-12
I have a desktop computer running 9.10 and have installed Amaya and love it and wish to also use it on my laptop running the exact same install (9.10 AMD64), but Amaya does not come up under Synaptic and/or Ubuntu Software Center on the laptop, and I can't even get it to run once I download the .deb directly from W3C.org, it will act as though it installs (kind of), but when I attempt to launch it nothing happens. If I launch it from the terminal it returns this:  Deleted Stale Lock File  -  Segmentation Fault ....  Any suggestions and or workarounds would be more than appreciated as I would like to use Amaya on both machines to work on a couple of sites that I am currently building and as of right now I have to work on the desktop in the living room.  Thanks in advance for any suggestions or comments.

---

### Post by byStanderone on 2010-01-12
...generally a segmentation fault occurs when certain dependencies are not satisfied. don't know the specifics of your laptop install, but you can update your system for a start. try sudo apt-get autoclean to clear your  system of binary clutter. goodluck!

---

### Post by akakingess on 2010-01-14
> **byStanderone said:**
> ...generally a segmentation fault occurs when certain dependencies are not satisfied. don't know the specifics of your laptop install, but you can update your system for a start. try sudo apt-get autoclean to clear your  system of binary clutter. goodluck!

Thanks for the assistance, but just to let you know, nothing that I did would get Amaya installed on that computer, however, I have it on another and will just build my sites from there and only there.

---

### Post by MountainX on 2010-01-28
same problem here. Amaya is not listed in Synaptic, and same result with apt-get from command line:

```
$ sudo apt-get install amaya
E: Couldn't find package amaya

```

Anyone know why?

---

### Post by MorleyPotter on 2010-10-14
Have you tried the .deb from w3c i have successfully installed and ran on 10.04?

---

