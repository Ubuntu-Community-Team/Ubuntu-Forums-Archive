---
title: "Choppy video and Software Center Freezes"
date: 2010-12-21
forum: General Help
---

### Post by X5-655 on 2010-12-21
After going back to Windows 7, I attempted linux again, but this time I was greeted with some nasty bugs.  And I have tried reinstalling multiple times, I can't find whats causing this.

Video performance is choppy and just terrible..  DVD's keep dropping almost 60% of their frames..  Ubuntu Software Center keeps freezing near the end of an install (though does seem to actually finish), and then maxes out CPU and causes my laptop to heat up a lot..

Ubuntu 10.10 64-bit
AMD Athlon II 2GHz Dual Core
4GB RAM
ATI Radeon (I don't know off hand which model)

I have tried open source drivers and FGLRX (which holy crap ATI fixed the tearing I see!), but nothing fixes it..  Other distros are not having these issues.

---

### Post by wojox on 2010-12-21
To find out witch model in a terminal run:

```
lspci | grep VGA
```

That's what's more than likely causing your issues.

---

### Post by X5-655 on 2010-12-21
> **wojox said:**
> To find out witch model in a terminal run:

```
lspci | grep VGA
```

That's what's more than likely causing your issues.
But why does it not affect any other distro?  Only ONE media player will play full speed, the built in "Movie Player" is the only player that'll play full speed..

I would like to add that I did a search on this forum and found countless others running 10.10 having the same issue, seemingly pointing to pulse audio as the culprit..


01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]

---

### Post by wojox on 2010-12-21
Maybe [fully remove -fglrx and reinstall -ati from scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch") would help.

---

### Post by X5-655 on 2010-12-21
> **wojox said:**
> Maybe [fully remove -fglrx and reinstall -ati from scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch") would help.

It does it on the open source driver, I said this already, not to mention, installing multiple times.

Besides, if I use open source, I can't play OpenGL games like Quake 4, they don't load at all, and require FGLRX.

Sorry, but 10.10 just stinks..  People with Intel and Nvidia are seeing the same problem as what I see in this thread:  [http://art.ubuntuforums.org/showthread.php?t=1592120](http://art.ubuntuforums.org/showthread.php?t=1592120)

---

### Post by X5-655 on 2010-12-21
Wow, install FGLRX 10.12, and now X won't even start..  Yea, just how I remember Linux, wasting my nights just trying to setup, only for the damned thing to get hosed..

Going back to Windows, the only OS that hasn't given me THIS much trouble.

---

### Post by X5-655 on 2010-12-23
This is so typical of the Ubuntu forums..  Problems get ignored..

I installed a PPA source to get the newer FGLRX and newer X-Servers, and the problem still exists..  This is foolish, a simple MPG video shouldn't be dropping 50% of it's frames.

---

### Post by PhantmKllr on 2010-12-23
Try installing the drivers from the AMD website.

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx")

---

