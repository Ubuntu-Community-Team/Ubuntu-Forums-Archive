---
title: "Ubuntu causing overheating?"
date: 2010-05-19
forum: General Help
---

### Post by Garglewithwater on 2010-05-19
On my desktop, I noticed that I can run Windows Vista for over 12 hours straight with only the occasional uprising in the sound of the fan, but when I run Ubuntu, the fan is blaring constantly, and I can only run it for about 3 hours before it shuts down from overheating. Is this a bug, and is there a fix?

---

### Post by amite on 2010-05-19
it is all good if you tell about your system config.,specially os version and your processor.it would help other to figure out your problem.

As i am using ubuntu 9.10 on my laptop [intel dual-core T4200 @2.00GHz,2gb ram] and i use it sometimes for more than 12 hours but never felt any heating problem.So i think it is not a bug but if u r using lucid i can't say anything.  

mention all these information it may help other to figure out ur problem..

---

### Post by hawthornso23 on 2010-05-19
I'd look first at the video drivers. The open source drivers, while they are improving, don't conserve power as well as the proprietary ones. If you think this might be the issue, install the proprietary drivers and see if it makes a difference.

---

### Post by squiddy on 2010-05-19
> **hawthornso23 said:**
> I'd look first at the video drivers. The open source drivers, while they are improving, don't conserve power as well as the proprietary ones. If you think this might be the issue, install the proprietary drivers and see if it makes a difference.

propietary driver helps a lot. at least with my laptop, it reduceses the heat.

---

### Post by Soul-Sing on 2010-05-19
To be honest, linux isn't that good at power management on laptops. Power management is a fairly complicated matter.
Linux could stress your harddisk also.

---

### Post by Dkkline on 2010-05-19
This is the 2end overheating message I've seen today..., anyway try this one [http://ubuntuforums.org/showthread.php?t=1484794]("http://ubuntuforums.org/showthread.php?t=1484794")

---

### Post by 3rdalbum on 2010-05-19
Is there a process taking up a lot of CPU power? Try checking the System Monitor to see if there is.

---

### Post by Garglewithwater on 2010-05-19
Well, my System specs are, 
AMD Phenom X3 8450(2.1GHz)
NVIDIA GeForce 6150 SE
4GB Ram DDR2
Running 10.4 and Vista.

I am using the proprietary drivers, the latest one.
No Process taking up a lot of CPU power.

---

### Post by hawthornso23 on 2010-05-19
You can sometimes get overheating if the thermal control information is incorrect in the DSDT table in your BIOS. This used to be a big issue but is not so common these days. Try 

```
dmesg | grep ACPI
```

and look for any warnings that mention things like thermal zones or fan control. That could be a sign that you have a buggy DSDT table. If you see temperature related warnings check whether you have the latest BIOS for your motherboard. 

If you have no problems in Vista, this probably isn't a dusty fan. However vacuuming is always a good idea when you have overheating.

---

