---
title: "Problems with Dell Latitude D600 laptops"
date: 2006-06-16
forum: General Help
---

### Post by huygens on 2006-06-16
Hy All,

This thread might only interest you if you have a laptop like the Dell Latitude D600.

Several problems have been reported, which seem to affect only a subset of all of this laptop users. The problems identified (source: [https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD600](https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD600)) are:
[LIST]
[*]CPU scaling ([#36014]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36014"))
[*]Sleep mode
[*]IRDA (infrared)
[*]Glithes on external display
[*]3D problems
[*]CPU soft lock-up ([#50683]("https://launchpad.net/distros/ubuntu/+source/xorg/+bug/50683"))
[/LIST]

Instead of trying to discuss this using the wiki page, I thought better to use a forum thread.

Therefore, here are my information concerning those issue on my laptop:
[LIST]
[*]CPU scaling: OK
[*]Sleep mode: OK
[*]IRDA: not tested yet. I have to figure out...
[*]External display: OK (see "Note 1" though on the wiki)
[*]3D: poor driver support but poor hardware anyway... ([Radeon Mobility 9000 seemingly supported]("http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL#Cards_seemingly_unsupported"))
[*] CPU soft lock-up: it occurs to me only when I am at my parents place (and thus using WiFi) and on battery or charging my battery...
[/LIST]

My configuration, so things are clear:
[LIST]
[*]Dell Latitude D600 - BIOS revision A12
[*]Intel Centrino Technology 1.6GHz (scaling from 600MHz to 1.6GHz), see below for cpuinfo
[*]1GB RAM - 30GB HD Hitachi (making lots of *weird* noise, but on Windows also...)
[*]ATI Radeon Mobility 9000 (poor hardware!!!)
[*]Ubuntu 6.06 Desktop (installed from scratch using Ubuntu Dapper Flight 5, and since then constantly upgraded)
[*]kernel 2.6.15-25-386
[*]Using Open Source video drivers (using the binary ones from ATI does not particularly improve my experience, and then Celestia crashes with the latest)
[*]Using LVM for partitioning and ext3, XFS and JFS inside (depending of the partition usage)
[*]No extra add-ons package from the Ubuntu release apart from the KDE desktop (but currently not using it)
[/LIST]

cpuinfo returned this:
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 9
model name      : Intel(R) Pentium(R) M processor 1600MHz
stepping        : 5
cpu MHz         : 599.577
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe est tm2
bogomips        : 1200.10
```

So, I do not have solution for the problems reporter by ConstantineEvens and PiotrGawrysiak. But at least, we could find out by sharing our hardware information what could cause the behaviour differences.

Cheers,
Hyugens

---

### Post by FuturePast on 2006-06-20
Hi Hyugens,

I am also having *major* problems with my Dapper install on a Latitude D600.
Random freezes, CPU soft lock-ups, problems suspending.
I have to disable the ethernet card in BIOS just to get more than a couple of minutes out of it.

It's a basic install, upgraded from Breezy.

I'm now writing this on my laptop from Dapper Live CD beta 2.
Kernel is 2.6.15-21-386.
xserver-xorg is 7.0.0-0ubuntu32.

It's rock solid. I can even suspend and resume the live CD.

What's going on??

---

### Post by FuturePast on 2006-06-20
Oh, I've tried BIOS A15 and A16.
Now on A16.

---

### Post by CujoQuarrel on 2006-06-20
I've not had any major problems yet. The only thing that was off was the screen resolution. It defaulted to max (1900x???) with no options to change. Worked around it but still not able to get the resolution I'm looking for.

---

### Post by FuturePast on 2006-06-20
I have just installed from the Dapper LiveCD Beta 2 and I finally have a working computer again.

Yipee!

---

### Post by JonD25 on 2006-06-21
[QUOTE=FuturePast]Hi Hyugens,

I am also having *major* problems with my Dapper install on a Latitude D600.
Random freezes, CPU soft lock-ups, problems suspending.
I have to disable the ethernet card in BIOS just to get more than a couple of minutes out of it.

It's a basic install, upgraded from Breezy.

I'm now writing this on my laptop from Dapper Live CD beta 2.
Kernel is 2.6.15-21-386.
xserver-xorg is 7.0.0-0ubuntu32.

It's rock solid. I can even suspend and resume the live CD.

What's going on??[/QUOTE]

I'm having the same problems. I get soft lock-ups, problems suspending, and I was just typing this response earlier and the computer just froze on me. I'm now in Windows retyping everything.

I have Ubuntu 6.06 installed with the live CD and it's completely up to date with the latest kernel. I'd hate to have to reinstall. How can I fix these problems? Because otherwise, I'll have to stay in Windows when I'm on this computer.

---

### Post by FuturePast on 2006-06-21
[QUOTE=JonD25] I'd hate to have to reinstall. How can I fix these problems? [/QUOTE]

I just want to make it clear, I re-installed using *not* the latest Live CD.
Something happened between Beta 2 and the final release that broke Ubuntu on the D600.

I will try to discover whether it's the kernel, X or acpi or something else.

Now running with (latest) kernel 2.6.15-25-386 - all fine.

---

### Post by JonD25 on 2006-06-21
[QUOTE=FuturePast]I just want to make it clear, I re-installed using *not* the latest Live CD.
Something happened between Beta 2 and the final release that broke Ubuntu on the D600.

I will try to discover whether it's the kernel, X or acpi or something else.

Now running with (latest) kernel 2.6.15-25-386 - all fine.[/QUOTE]

So are you saying I should get ahold of a beta CD? If the new kernel is working for you, then that can't be my problem since I'm also running it. If anything that's my problem. I still have the last kernel to boot from, so I'll see if going back fixes everything.

---

### Post by FuturePast on 2006-06-21
[QUOTE=JonD25]So are you saying I should get ahold of a beta CD? If the new kernel is working for you, then that can't be my problem since I'm also running it. If anything that's my problem. I still have the last kernel to boot from, so I'll see if going back fixes everything.[/QUOTE]

Getting a beta Dapper CD is not the solution. All I'm saying is that that particular version of Ubuntu works but the up-to-date system doesn't.

I'm trying to follow a process of elimination (i.e. what can I upgrade without breaking my system again.)
I've now running a completely upgraded system apart from:
xserver-xorg (7.0.0-0ubuntu32)
xserver-xorg-core (1:1.0.2-0ubuntu6)
xserver-xorg-driver-all (7.0.0-0ubuntu32)
xserver-xorg-driver-ati (1:6.5.7.3-0ubuntu5)
xserver-xorg-driver-i810 (1:1.4.1.3-0ubuntu3)

I think I'll make a support ticket on Launchpad abou this now.

---

### Post by JonD25 on 2006-06-21
Gotcha. Well, if you find a solution or if it gets fixed with another update, let me know. I'm using the last kernel right now, and it seems to be working ok so far, but I don't know for sure. I'll have to use it for a while to see if I get any soft lock-ups, freezing, and try suspending to see what happens. This could be a temporary solution, but I'd obviously like to be running an up to date system. Thanks though.

---

### Post by FuturePast on 2006-06-21
No problems. 

Was your mouse moving really jerkily as well?

---

### Post by huygens on 2006-06-21
[QUOTE=JonD25]I get soft lock-ups, problems suspending[/QUOTE]

Happy to hear I am not the only one getting soft-lockup. During the Dapper testing, I thought I was alone :(
At least, with every new update since the early beta, it has been improving and now it occurs only when I am connected to the wireless network of my parents. I have tried another wireless at work, but it did work flawlessly... While at my parents after a dozen minutes, the CPU soft lockup triggers...

---

### Post by JonD25 on 2006-06-22
[QUOTE=FuturePast]No problems. 

Was your mouse moving really jerkily as well?[/QUOTE]
Only during soft lock-ups. Otherwise, it seems to work perfectly fine

By the way, as I figured, it has nothing to do with the new kernel, as it froze on me again. I'm just going to wait till this gets fixed before booting back in to Ubuntu and I'll just use *shudder* Windows on this for now. Luckily I also have an iMac, so I don't need to stay in Windows all the time.

---

### Post by FuturePast on 2006-06-22
[QUOTE=FuturePast]I think I'll make a support ticket on Launchpad abou this now.[/QUOTE]

Opened bug #50683 in xorg on Launchpad. Please confirm.

Cheers

[https://launchpad.net/distros/ubuntu/+source/xorg/+bug/50683]("https://launchpad.net/distros/ubuntu/+source/xorg/+bug/50683")

---

### Post by JonD25 on 2006-06-22
[QUOTE=FuturePast]Opened bug #50683 in xorg on Launchpad. Please confirm.

Cheers

[https://launchpad.net/distros/ubuntu/+source/xorg/+bug/50683]("https://launchpad.net/distros/ubuntu/+source/xorg/+bug/50683")[/QUOTE]
Sorry, I'm unfamiliar with Launchpad. How do I confirm?

---

### Post by huygens on 2006-06-23
[QUOTE=JonD25]Sorry, I'm unfamiliar with Launchpad. How do I confirm?[/QUOTE]
I think you or I cannot "confirm" the bug. At least I did not find a way to do this. So I guess only one of the package responsible can confirm the bug, or ask for information if this isn't sufficient, etc.
You just have to wait and see :)

Huygens

---

### Post by FuturePast on 2006-06-23
[QUOTE=JonD25]Sorry, I'm unfamiliar with Launchpad. How do I confirm?[/QUOTE]

Sorry, they seem to have changed the permissions; it used to be possible for all users to confirm and change importance and things.

---

### Post by JonD25 on 2006-06-27
I noticed your post on launchpad that you fixed it. I tried duplicating it as best I could be removing some or reinstalling xserver-xorg stuff. Didn't work. I dunno what to do.

---

### Post by huygens on 2006-08-14
It seems that some of the problem (CPU soft lock-up, crash and DHCP problems) I had were hardware oriented, as I started to get them also on Windows. I call Dell and it seems that my motherboard and keyboard need to be changed.
Once done (hopefully tomorrow), I will check if I still have those annoyances.

Huygens

---

