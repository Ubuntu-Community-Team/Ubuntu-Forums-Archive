---
title: "Will nvidia FX5500 AGP work on Ubuntu 11.04"
date: 2011-07-21
forum: General Help
---

### Post by AgentZ86 on 2011-07-21
Hi

I'm need an AGP card that will work on 64 bit 11.04 ubuntu. out of box and using the nvidia proprietary drivers by default.

I don't want to have to turn of xserver and install some driver.

I have the FX4000 now and cannot figure out how to turn off x server and install the driver so I figured a cheap replacement with support in 11.04 would be easier and simpler when upgrading etc. 

Will the FX 5500 AGP card work out of the box with no configuration for a fresh install of 11.04 64 bit ubuntu ?

Please advise
Thanks

---

### Post by seawolf167 on 2011-07-21
You'll have to install the drivers regardless.

You can either install the proprietary driver from Nvidia, the link to which is [here]("http://www.nvidia.com/object/linux-display-amd64-275.21-driver.html"). Or install the driver from "Additional Drivers" by clicking the power button in the upper-right corner of the screen, selecting "System Settings" then selecting "Additional Drivers".

To stop the x server, simply type

```
sudo service gdm stop
```

then when finished, start it with

```
sudo service gdm start
```

---

### Post by AgentZ86 on 2011-07-27
> **seawolf167 said:**
> You'll have to install the drivers regardless.

You can either install the proprietary driver from Nvidia, the link to which is [here]("http://www.nvidia.com/object/linux-display-amd64-275.21-driver.html"). Or install the driver from "Additional Drivers" by clicking the power button in the upper-right corner of the screen, selecting "System Settings" then selecting "Additional Drivers".

To stop the x server, simply type

```
sudo service gdm stop
```

then when finished, start it with

```
sudo service gdm start
```

Does not work.

I've tried several variation of commands that will stop/start gdm and it goes to the consol and is trying to complete scripts with the [OK] next to some of the lines but then sits there at the next line and never completes something so no consol access.

I tried to boot to recovery mode and attempted the same but NOPE

So I ditched installing the driver for now and purchased a GS8400 PCI card and the 3D is installed and working but 11.04 has other issues I'll post in another thread.

Thanks for the help and it turns out that the FX4000 card regardless of not being able to get the proper driver installed is not the problem cause I have another issue that the GS8400 card with the installed drivers did not solve.

I suspected the card since it appeared to be graphics related but NOPE it's something else so I'll post on this new topic now that I know it's not hardware and not driver related.

Thanks

---

