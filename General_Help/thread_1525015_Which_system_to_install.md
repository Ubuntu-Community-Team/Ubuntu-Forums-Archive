---
title: "Which system to install????"
date: 2010-07-06
forum: General Help
---

### Post by ksadil on 2010-07-06
I am going to upgrade my Hardy(8.04) system to 10.04, but after last time I am cautious about which system to install.

My system is a dual core Athalon 64 pc that I use as a server. The OS has worked flawlessly for years now, very happy. The system I installed  was the AMD64  version and found that some applications would not run, and 64 bit packages were not available for other applications. Then I did not want to ditch my investment setting the system up, so I stuck with the AMD64.

Is this still the case with the AMD64 Ubuntu 10.04? Should I just use the i386 installer and have access to the latest and greatest? Any advice would be appreciated.

---

### Post by Leppie on 2010-07-06
64 bit support is improving all the time.
what applications would you like to install?

---

### Post by ksadil on 2010-07-06
For now:
Virtualbox with linux and windows7 guest, citadel, samba shares, apache, ipp printers, picasa, back in time, nx server.

Probably tomorrow:
latest new stuff

I guess I can run a 32 bit ubuntu vm for anything that is not supported

---

### Post by Leppie on 2010-07-06
yes, that would be an option.
you could also install the ia32-libs library (32 bit compatibility).

---

### Post by ksadil on 2010-07-06
It was a while ago that I tried this on my current setup. I don't remember how it worked out, but I accidentally tried to install a 32 bit deb recently and it complained about incorrect architecture. This is bringing back uncomfortable memories. 

Is there any stats to say how much performance gain I am giving away if I install the 32bit version?

---

### Post by philinux on 2010-07-06
> Is there any stats to say how much performance gain I am giving away if I install the 32bit version?

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

### Post by Leppie on 2010-07-06
i'm not sure he'll want to encode ogg vorbis or do 3d rendering on his server.
the major improvement in 64 bit would be with apache.
a lot of 64 bit packages are only compiled on 64 bit machines, hence they do not contain any 64 bit specific instructions.

---

### Post by philinux on 2010-07-06
It's interesting that the ubuntu website says of the desktop edition.

> 64-bit - Not recommended for daily desktop usage

But for the server edition.

64-bit &#8211; Recommended for most users
[http://www.ubuntu.com/server/get-ubuntu/download](http://www.ubuntu.com/server/get-ubuntu/download)

There's a bug raised for the desktop wording. Seems OTT.

---

### Post by ksadil on 2010-07-06
> **philinux said:**
> [http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

Thanks philinux. Exactly what I needed. This runs as a small server. No music encoding or 3d work. I might take the 32 bit route.

---

### Post by ksadil on 2010-10-28
Well I bought a shuttle xpc sn78sh7 with a phenom cpu, and it is fast once it starts, but it can just sit there for a minute while starting with nothing happening.

I am not sure about the stability of the video driver either (downloaded from nvidia). Sometimes the screen just freezes while watching something on youtube, or closing down a web browser.
Other times the system just turns off in a flash while rendering a video using pitivi. No faults seem reproducable, it is infrequently unstable (3 times per day typically) :(

GeForce 8200 using version 195.36.24

It was much worse before I flashed the bios!

I can't help but feel I made a mistake buying that hardware to use as a server hosting virtualbox vm's

---

### Post by rajeevisonline on 2010-10-28
I agree with you..nvidia drivers for linux is totally bad... its generic

---

### Post by ksadil on 2010-10-28
Ths slow startup I can handle, but the crashing is painful. It turns out though the crashing may be caused by adobe flash player, so as a server it will not be using that software. 

Nvidia used to be so good on linux, I know there was always polotics, but I always had good results compared to SIS. Any guidance on buying a graphics card for this AMD64 machine? It might solve half these problems. ATI maybe???

---

### Post by mcduck on 2010-10-28
> **ksadil said:**
> Ths slow startup I can handle, but the crashing is painful. It turns out though the crashing may be caused by adobe flash player, so as a server it will not be using that software. 

Nvidia used to be so good on linux, I know there was always polotics, but I always had good results compared to SIS. Any guidance on buying a graphics card for this AMD64 machine? It might solve half these problems. ATI maybe???

most likely the startup is actually running fine, it's just that Plymouth (that handles the loading screen) doesn't stop to wait if your graphics card takes along time to switch to suitable graphic mode, and instead just continues booting and tries again later. (as a result you'll see black screen with a blinking cursor for most of the boot process, and then briefly the loading screen before the desktop/login screen loads).

It's possible to force Plymouth to wait for your graphics card, which would give you the loading screen for the whole boot process but it wouldn't make the boot any quicker, more of the opposite.

---

### Post by ksadil on 2010-10-28
Plymouth... At times it has been sitting there for 10 minutes with cursor blinking. Power off and try again and next time it is 40 seconds. It is a bit like driving an old unreliable car wondering when it is going to have an issue. 

Would a more compatible card solve this problem? It does not have to be cutting edge, but I do want 3d for flight gear. And it must be 64 bit compatible. I see  similar andt ATI posts, just like anti nvidia posts, but they are the most commonly available.

---

### Post by mcduck on 2010-10-29
Well, if you sometimes have to wait *10 minutes*, then you have a *real* problem and it's not just issue of Plymouth not showing you pretty graphics.

(like I said, the plymouth glitch doesn't slow down the boot, it just doesn't display the graphics from the beginnig of boot. So if the boot is really slow there must be some actual problem causing that. I just mentioned the Plymouth glitch since quite many people who get it on their computers think the computer is frozen during the time they only see the blinking cursor, and you didn't mention occassional 10-minute wait before this.)

..but actually getting the graphics to work might help you a bit, it will not speed up your boot but you might be able to see some error message or something that tells you what the actual cause for slow boot is.

```
echo "FRAMEBUFFER=y" | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u
```

Of course booting to the recovery mode a couple of times would work even better, as you'll see a lot more detailed info about boot process that way.

---

### Post by ksadil on 2010-10-29
Cool, thanks. We are getting somewhere :)

I tried recovery  and this is what I found

```
Oct 25 06:14:08 ubuntu kernel: [    0.023488] ACPI: Core revision 20090903
Oct 25 06:14:08 ubuntu kernel: [    0.040006] ftrace: converting mcount calls to 0f 1f 44 00 00
**Oct 25 06:14:08 ubuntu kernel: [    0.040009] ftrace: allocating 22538 entries in 89 pages**
Oct 25 06:14:08 ubuntu kernel: [    0.050062] Setting APIC routing to flat
Oct 25 06:14:08 ubuntu kernel: [    0.050522] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 25 06:14:08 ubuntu kernel: [    0.185045] CPU0: AMD Phenom(tm) II X4 965 Processor stepping 03
[B]Oct 25 06:14:08 ubuntu kernel: [    0.190000] Booting processor 1 APIC 0x1 ip 0x6000
Oct 25 06:14:08 ubuntu kernel: [   15.567513] Booting processor 2 APIC 0x2 ip 0x6000
Oct 25 06:14:08 ubuntu kernel: [   30.951297] Booting processor 3 APIC 0x3 ip 0x6000[/B]
Oct 25 06:14:08 ubuntu kernel: [   46.340524] Brought up 1 CPUs
Oct 25 06:14:08 ubuntu kernel: [   46.340526] Total of 1 processors activated (6800.96 BogoMIPS).
```

The bold rows are slow.

It does not show it here in var/log/messages, but watching it in recovery, each of the processors 1,2&3 show "not responding"

After that it is all fast.

Do I need some special boot flags?

---

### Post by ksadil on 2010-10-29
I tried different combinations of noapic and nolapic

nolapic solves the problem of processors not responding, but the first delay is still there.

---

### Post by ksadil on 2010-10-29
and half my temperature sensors do not work now, even if I restore grub back to original :(

Oh well fixed half the boot speed issue

---

### Post by ksadil on 2010-11-01
Running out of options here, so I tried Linux Mint 9 i386.

The installation went much more quickly and boots very fast. It still locks up occasionally. I think flashplayer is the culprit.

I will try doing all my youtube viewing in a virtualbox guest with another os. Is this a valid test, or am I wasting time?

---

