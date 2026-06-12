---
title: "This driver is activated but not currently in use"
date: 2011-05-01
forum: General Help
---

### Post by Finalfantasykid on 2011-05-01
I am trying to get my new computer to work with the proprietary nvidia drivers, but unfortunatly I am having some troubles.  When I activate the nvidia drivers in jockey and restart the computer, the DE fails to load unity, and no compositing is actually being done.  When I check jockey, it says:

"this driver is activated but not currently in use"

I have an NVIDIA GT 550M.  I can use unity with nouveau, however there are some problems that I have noticed, like not resuming from sleep and some freezing, which I suspect is a result of the open source drivers(could be fixed in an update later).  But does anyone know how to get the proprietary drivers to work in the mean time?

---

### Post by grahammechanical on 2011-05-01
I have 10.10 on one partition and 11.04 on another. I have the Nvidia 260.19.06 driver activated on both installations. On 10.10 the message is activated and in currently use. On 11.04 the message is activated but not currently in use.

So, what is different between the two versions? On 10.10 I have enhanced visual effects working. On 11.04 I am using unity 2D. I have concluded that "driver activated" = driver being used. And "not currently in use" = you are not using 3D effects.

Is it possible to have Unity 3D? I do not know.

Regards.

---

### Post by Finalfantasykid on 2011-05-01
Thanks for the reply.  

I sort of thought of that as well, but it turns out this is not the case.  For example when I run nvidia-settings, it displays an error saying that there is no nvidia driver in use.  And when I try to run things like games, they fail to run.

---

### Post by emoguitarist06 on 2011-05-02
Sorry this is not answer to your question but just saying that I my Nvidia Ion (first gen) shows "this driver is activated but not currently in use" on 11.04

I did not "install" the driver myself but Ubuntu installed it durring 11.04 installation. I did a clean fresh install.

How do I know if I'm running 3D or 2D unity?
Plus is it supposed to say the driver is in use?

I don't know if I'm being paranoid but I believe I can hear my computer more in 11.04 than in 10.10

---

### Post by spikoley on 2011-05-08
It sounds like this [bug]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788").  Make sure you update the bug.

---

### Post by orn on 2011-06-07
> **emoguitarist06 said:**
> Sorry this is not answer to your question but just saying that I my Nvidia Ion (first gen) shows "this driver is activated but not currently in use" on 11.04

I did not "install" the driver myself but Ubuntu installed it durring 11.04 installation. I did a clean fresh install.

How do I know if I'm running 3D or 2D unity?
Plus is it supposed to say the driver is in use?

I don't know if I'm being paranoid but I believe I can hear my computer more in 11.04 than in 10.10

I'm having the same problem. It says the driver isn't being used. I've tried all the tricks mentioned on the forums that I've found but nothing works.

To answer your question, unity doesn't run unless it's 3d enabled, but I am certain the ION hardware acceleration isn't in use. I'm using an ION HTPC and after upgrading to 11.04 HD videos are really choppy and videos in general.

Did you ever figure out how to fix this?

---

### Post by airspoon on 2011-06-07
I have been having the same issue. I'm new to Ubuntu but have been reading a lot about this issue and I have yet to find a solution, other than to go without 3d effects and Unity. From my understanding, the only work-around is to use Gnome-Classic. Does anyone know of anything different and could the Ubuntu team be working on this issue?

---

### Post by orn on 2011-06-07
> **airspoon said:**
> I have been having the same issue. I'm new to Ubuntu but have been reading a lot about this issue and I have yet to find a solution, other than to go without 3d effects and Unity. From my understanding, the only work-around is to use Gnome-Classic. Does anyone know of anything different and could the Ubuntu team be working on this issue?

Unity is actually working for me, but 3d acceleration isn't.

---

### Post by iDVB on 2011-06-08
Same issue:
**This driver is activated but not currently in use.**

Personally, I've had experience working with this setup from 9.04 - 10.04 and I've NEVER been able to get video to play correctly just in VLC Player.  I've only gotten it to work well on that setup but in the XBMC app and for that I had to [http://tinyurl.com/2u9zrpz](http://tinyurl.com/2u9zrpz)

**My Setup:**
ZBox HD ID11
Intel NM10 Express w/ Atom D510 (Dual core, 1.66GHz)
NVIDIA Next-Generation ION w/ 512MB DDR3 memory
2GB RAM
30 GB SDD
Ubuntu 11.04

[[IMG]http://img7.imagebanana.com/img/abpdb3tt/thumb/AdditionalDrivers_001.png[/IMG]]("http://www.imagebanana.com/view/abpdb3tt/AdditionalDrivers_001.png")

---

### Post by orn on 2011-06-09
> **iDVB said:**
> Same issue:
**This driver is activated but not currently in use.**

Personally, I've had experience working with this setup from 9.04 - 10.04 and I've NEVER been able to get video to play correctly just in VLC Player.  I've only gotten it to work well on that setup but in the XBMC app and for that I had to [http://tinyurl.com/2u9zrpz](http://tinyurl.com/2u9zrpz)

**My Setup:**
ZBox HD ID11
Intel NM10 Express w/ Atom D510 (Dual core, 1.66GHz)
NVIDIA Next-Generation ION w/ 512MB DDR3 memory
2GB RAM
30 GB SDD
Ubuntu 11.04

[[IMG]http://img7.imagebanana.com/img/abpdb3tt/thumb/AdditionalDrivers_001.png[/IMG]]("http://www.imagebanana.com/view/abpdb3tt/AdditionalDrivers_001.png")

Presumably you are using compiz as a window manager then?

---

### Post by iDVB on 2011-06-14
> **orn said:**
> Presumably you are using compiz as a window manager then?

Sorry, ya, I've tried with and without compiz and I still get that error in the driver window. Additionally, everything seems to be running shitty. I mean, definitly not a smoothly as when I've seen the proper NVIDIA driver beening used.

Any more word on this issue?

D

---

### Post by wildmanne39 on 2011-06-15
> **iDVB said:**
> Sorry, ya, I've tried with and without compiz and I still get that error in the driver window. Additionally, everything seems to be running shitty. I mean, definitly not a smoothly as when I've seen the proper NVIDIA driver beening used.

Any more word on this issue?

DHi, it saying that it is not in use is a bug it really is in use if you activated it and you see the green dot by it, I have the same issue and I have been running natty since beta and I have the cube and many effects working good even though it says it is not in use because it really is.

---

