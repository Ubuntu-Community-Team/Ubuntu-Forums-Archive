---
title: "Ubuntu 11.10 Not very responsive"
date: 2012-02-21
forum: General Help
---

### Post by ChemMeister on 2012-02-21
I dont know if anyone else is experiencing this. But ever since i installed Ubuntu 11.10, i notice that it is not too responsive, basically when i double click on a icon to open  an application such as firefox or a terminal. It doesn't open "instantaneously" there is always "a certain lag" of 1-2 seconds. This is particularly weird because i  have a dell Aurora R3 i7-2600K @ 4.1 GHZ 16GB of RAM. Windows 7 on the hand is very fluid. Any ideas why this is the case. Thanks

---

### Post by roelforg on 2012-02-21
Not sure,

I'd like to help but my pc runs 11.10 server opon which i installed the GUI (it's exactly like it want it, normal ram usage: 200 mb, CPU: Pentium IV), so i can't reproduce such a thing.

Though...
I'd check your hd, linux needs to load the app from your HD in to memory, that's the biggest bottleneck i can think of.
(PS: Firefox needs a few secs to boot on any os, try installing it on win7 and proof it doesn't need those 3 secs on win7)

---

### Post by Hylas de Niall on 2012-02-21
> **roelforg said:**
> Not sure,

I'd like to help but my pc runs 11.10 server opon which i installed the GUI (it's exactly like it want it, normal ram usage: 200 mb, CPU: Pentium IV), so i can't reproduce such a thing.

Though...
I'd check your hd, linux needs to load the app from your HD in to memory, that's the biggest bottleneck i can think of.
(PS: Firefox needs a few secs to boot on any os, try installing it on win7 and proof it doesn't need those 3 secs on win7)

I noticed that it's a lot slower than the old Gnome 2 Ubus, but i think it's prolly more to do with Gnome 3 than Ubuntu, TBH.
(i am of course guessing at that, it's just an observation after moving back to a much speedier Ubu 10.10)

---

### Post by roelforg on 2012-02-21
I'm gonna advise you to try LXDE, i use it and it is a lot faster that the normal one.
I attached a screenshot of my pc.

---

### Post by ChemMeister on 2012-02-21
> **roelforg said:**
> Not sure,

I'd like to help but my pc runs 11.10 server opon which i installed the GUI (it's exactly like it want it, normal ram usage: 200 mb, CPU: Pentium IV), so i can't reproduce such a thing.

Though...
I'd check your hd, linux needs to load the app from your HD in to memory, that's the biggest bottleneck i can think of.
(PS: Firefox needs a few secs to boot on any os, try installing it on win7 and proof it doesn't need those 3 secs on win7)

Firefox is just an example, it is pretty much the same thing for software center.
I had it installed on an older hard drive that i had from two years ago, and then i bought a new hard drive 
[B][SIZE=1]Western Digital Caviar Blue 500 GB SATA III 7200 RPM, and still faced the same problem.
[/SIZE][/B]

---

### Post by roelforg on 2012-02-21
I know that both firefox and softwarecenter use a lot of mem because they are just big apps;
try loading a pdf file with adobe reader in windows and check task manager, you'll be amazed by the mem it uses.

---

### Post by roelforg on 2012-02-21
> **ChemMeister said:**
> Firefox is just an example, it is pretty much the same thing for software center.
I had it installed on an older hard drive that i had from two years ago, and then i bought a new hard drive 
[B][SIZE=1]Western Digital Caviar Blue 500 GB SATA III 7200 RPM, and still faced the same problem.
[/SIZE][/B]
It can be a number of things.
To many to name.
HD's are the most common, memspeed/cpuspeed and other speeds/bandwidths inside the system can cause this as well.

---

### Post by efflandt on 2012-02-21
You might also compare boot times.  Windows probably uses many dll's shared among its programs, so it loads much more when booting than Linux does.  For example 64-bit Win7 on an 8 GB PC is using 3.7 GB when it finishes booting vs. roughly 700 MB for 64-bit 11.10.

So certain applications in Linux may need to load libs.  Once they are in RAM cache, they should load much quicker.

But you are complaining about 1-2 seconds.  My old PC running 64-bit 10-04 on early Athlon64 3200+ (2 GHz) takes much longer to load OpenOffice Writer than the few seconds it takes to start LibreOffice Writer in 11.10 on my newer PC, (only 1 second to reload).

BTW, you do not need to double click apps in the unity bar, so maybe there is a built-in delay to avoid opening more than one copy of a program at the same instant if someone does that (I know firefox used to complain if you double clicked its icon in earlier Ubuntu versions and 2 instances tried to open simultaneously).

---

### Post by ChemMeister on 2012-02-21
> **efflandt said:**
> You might also compare boot times.  Windows probably uses many dll's shared among its programs, so it loads much more when booting than Linux does.  For example 64-bit Win7 on an 8 GB PC is using 3.7 GB when it finishes booting vs. roughly 700 MB for 64-bit 11.10.

So certain applications in Linux may need to load libs.  Once they are in RAM cache, they should load much quicker.

But you are complaining about 1-2 seconds.  My old PC running 64-bit 10-04 on early Athlon64 3200+ (2 GHz) takes much longer to load OpenOffice Writer than the few seconds it takes to start LibreOffice Writer in 11.10 on my newer PC, (only 1 second to reload).

BTW, you do not need to double click apps in the unity bar, so maybe there is a built-in delay to avoid opening more than one copy of a program at the same instant if someone does that (I know firefox used to complain if you double clicked its icon in earlier Ubuntu versions and 2 instances tried to open simultaneously).

Windows 7 is about 2 seconds faster on boot. Ubuntu 10.04 was much faster even on older machines. Overall i am really disappointed with Ubuntu 11.10, it is a worse system

---

### Post by LinuxFan999 on 2012-02-21
Do you have the latest updates?

By the way, Ubuntu 11.10 is very fast on my computer. It is faster than Vista was on the same system, although boot and shutdown times are almost the same.

---

### Post by ayozito on 2012-02-21
After one week trying 11.10 and LM12, tomorrow I will change to 10.04 again.

10.04 is the best stable version now, both Ubuntu and Linux Mint rushed for new versions and they are too much unstable. Unity and Gnome Shell crash too much.

---

