---
title: "Clues please! Failed to retrieve device info"
date: 2009-12-18
forum: General Help
---

### Post by fizikz on 2009-12-18
```
Error: device.cpp|86: Failed to retrieve device info (Inappropriate ioctl for device, 25)
```

This is the error I get when I try to run the airclick program ([http://sourceforge.net/projects/airclick/](http://sourceforge.net/projects/airclick/)) to control the airclick remote + RF receiver. The receiver is recognized as 'hidraw0' in /dev, and it seems to be receiving input since I can see input upon keypresses if I do > sudo cat /dev/hidraw0

I've run out of ideas on how to solve this. Any suggestions?

Btw, this problem is on my Aspire One netbook running Crunchbang linux (based on Ubuntu).

---

### Post by dcstar on 2009-12-19
> **fizikz said:**
> ```
Error: device.cpp|86: Failed to retrieve device info (Inappropriate ioctl for device, 25)
```

This is the error I get when I try to run the airclick program ([http://sourceforge.net/projects/airclick/](http://sourceforge.net/projects/airclick/)) to control the airclick remote + RF receiver. The receiver is recognized as 'hidraw0' in /dev, and it seems to be receiving input since I can see input upon keypresses if I do 

I've run out of ideas on how to solve this. Any suggestions?

Btw, this problem is on my Aspire One netbook running Crunchbang linux (based on Ubuntu).

It probably means that the software is not compatible with Ubuntu (or whatever you are running). ioctl is IO control of the device.

---

### Post by fizikz on 2009-12-19
The software runs fine on my Ubuntu computer. The problem is on my netbook running a Ubuntu spinoff. I figured that closely related distros should be similar enough that, if necessary, with a bit of tweaking most things should work on either setup. For instance, the device file is named slightly differently in Crunchbang compared to Ubuntu, but I found this difference and changed the relevant lines in the application's config file. 

I'm trying to find some clues on how/what to modify to get it working. At this point I'm not sure exactly what the problem is and how to get more info on it to debug it. Is there a way to get a more verbose error message?

---

