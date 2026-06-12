---
title: "Questions about Intel graphics card &amp; Desktop Cube"
date: 2010-01-30
forum: General Help
---

### Post by NEXTLOVER on 2010-01-30
Hello. I hope this is the correct forum to post. If not, I am truly sorry. 

I've been using Linux for about 1wk. now & absolutely love it (I'm a native Windows user). I've read around that Intel graphics are basically a no-go in enabling the Desktop 3D cube. 

My graphics card is specifically this:
*-display               
       description: VGA compatible controller
       product: 82G33/G31 Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:29 memory:fe800000-fe87ffff ioport:c080(size=8) memory:d0000000-dfffffff(prefetchable) memory:fe700000-fe7fffff

... which I have no idea about LOL. I can enable Desktop Effects all right, the Shaky Windows, etc. except for the Cube. I don't have any proprietary drivers at all recognized in Ubuntu 9.10 (x64), and EnvyNG does not seem to work. EnvyNG doesn't even open up so I can't see which drivers are available to me. 

Is there a work-around for my scenario to enable the Cube? Any drivers I should install (NVIDIA drivers + Intel graphics card)? Or any other workarounds someone out there came up with?

Any advice/tips/suggestions/directions to tutorials/FAQs/videos would be greatly appreciated. & even if I don't have a cube, I'll still keep Ubuntu :D

---

### Post by chewearn on 2010-01-31
NVIDIA driver won't work with intel graphics.  There is no way to force NVIDIA driver into the system without breaking something.  It's like trying to run a car better by pouring water into the tank.

However, I'm sure Cube could work with Intel graphics.  I have a netbook with Intel graphics, and I have Cube working on it.  The exception is I cannot enable transparency on the Cube; that would cause the desktop to slow down and becomes unusable.

Perhaps, you could explain further want sort of problem you are seeing when Cube is enabled.

---

### Post by NEXTLOVER on 2010-02-01
The problem is I can't get the Cube to work at all. I've switched the settings to enable the cube, rotate the cube, disabling the Desktop wall, but it's still the same.

I'll still play around with the settings some more to see if it's just my settings that are messed up. 

Yeah, didn't think so about the NVIDIA drivers + Intel graphics card. So you do have an Intel graphics card & were able to have a Cube Desktop?

---

### Post by chewearn on 2010-02-01
> **NEXTLOVER said:**
> The problem is I can't get the Cube to work at all. I've switched the settings to enable the cube, rotate the cube, disabling the Desktop wall, but it's still the same.
Did you increase the number of workspaces from 2 (default) to 4.


> So you do have an Intel graphics card & were able to have a Cube Desktop?
Yes

---

### Post by t4thfavor on 2010-02-01
> **chewearn said:**
> NVIDIA driver won't work with intel graphics.  There is no way to force NVIDIA driver into the system without breaking something.  It's like trying to run a car better by pouring water into the tank.

However, I'm sure Cube could work with Intel graphics.  I have a netbook with Intel graphics, and I have Cube working on it.  The exception is I cannot enable transparency on the Cube; that would cause the desktop to slow down and becomes unusable.

Perhaps, you could explain further want sort of problem you are seeing when Cube is enabled.


It's more like trying to put an airplane motor into a submarine. Basically not possible.

I have integrated Intel G45 graphics (GMA450?) and it works OK. But nothing to write home about.

---

### Post by NEXTLOVER on 2010-02-02
I ended up uninstalling Wubi then reinstalling with a new downloaded iso again. But I've got the cube :D

I think it was the whole install process that just messed up my ability to have that wonderful Cube. It took a while for me; it kept hanging up & I'd have to start it all over again. I'm not sure; mebe bad iso or something.

Thanks for the help! I really appreciate it :)

---

