---
title: "Help With RAID (After the fact)"
date: 2009-07-31
forum: General Help
---

### Post by jlacroix on 2009-07-31
Hello everyone. I'm trying to help a colleague who confided in me with a tech problem he is trying to solve.

He is currently using Windows and has a NAS server set up with Windows. The RAID card is a Highpoint Rocketraid 2310 and I'm pretty sure that's a software raid card. 

Here's the setup. There are five drives in this box. One of them is reserved for the OS. The other four will be part of the raid and will store data only. (The OS is on the first drive, not the ones in the raid). What he wants to do essentially is get rid of Windows from the first drive, replace it with Ubuntu, and have Ubuntu handle the raid on the other four drives. (Mirroring with striping, I believe).

Here's the catch: He wants to convert this system to Ubuntu WITHOUT formatting the drives because they already contain almost a terabyte of data that would be difficult to back up. The data is already mirrored on each of the four drives.

At first I recommended mdadm, which I'm sure can handle the software raid. Unfortunately, the only instructions I found on my Google quest assumed that we are installing and setting up the RAID for the very first time. We're not. We're merely wanting to convert the OS drive to Ubuntu and leave the data on the 4 RAID drives intact. Setting up mdadm during Ubuntu installation with the alternate CD is the only way I've ever set up RAID on a Linux box.

This may be asking a lot, but can this be done?

---

### Post by jlacroix on 2009-08-03
Does anyone know? Maybe I posted this in the wrong forum? I would benefit from any knowledge anyone can provide and I'll be glad to answer any questions as best I can. Thank you!

---

### Post by realzippy on 2009-08-03
...it might be a fakeraid.
Have a look:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by jlacroix on 2009-08-03
> **realzippy said:**
> ...it might be a fakeraid.
Have a look:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I think it is Fake Raid. That howto only shows how to install Ubuntu onto a raid, how do I set up a RAID on four disks that are seperate from the OS drive?

---

