---
title: "Ubuntu crashing - hardware issue?"
date: 2010-02-28
forum: General Help
---

### Post by aabye on 2010-02-28
Hey all,
I am running Ubuntu 9.10 on a Dell 600m with 1.5 GHz, 1GB RAM, and 120 GB HDD. Not very long after updating to 9.10, Ubuntu started to "crash" just from being on. The way it crashes is the desktop image turns brown, and if I try to run a program a box comes up with "Error: Failed to execute child  process '[almost any program]' (input/output error)". However all open programs continue running and they run fairly stable. When I try to turn off, nothing happens, and when I then push the power button, the usual options come up, just this time there are no icons and there is no text, just a bunch of rectangles, so I have to turn off holding power button. 

I then turn it off and back on, and then it works well (until it repeats the process). I suspect that it might be a hardware problem, since the laptop is very old. I was wondering if there is a tool that can check if everything works well? Or if there is another fix to it?

Thanks a lot,
aabye

---

### Post by cjhabs on 2010-02-28
You can test the memory by running the tester from the live cd.
For additional help, check out:
[https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)

---

### Post by MooPi on 2010-02-28
The second test you may want to try is a file system check for the hard drive. Boot from the Live CD and open a terminal. ```
sudo fdisk -l
``` This will give you youe hard disk designation. Now plug that into where the **** correspond. Should be something Like ```
/dev/sda1 or /dev/sdb1
``````
e2fsck -n/dev/****
```

---

