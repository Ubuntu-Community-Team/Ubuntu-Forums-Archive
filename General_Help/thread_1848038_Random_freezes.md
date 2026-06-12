---
title: "Random freezes"
date: 2011-09-21
forum: General Help
---

### Post by Psy02 on 2011-09-21
I have Ubuntu 11.04 and have random freezes where someone I get CapsLock  and ScrollLock flashing and audio loops where SysRq keys don't work not  even reboot (alt + SysRq + b)

Windows XP 64 has no errors and no freezing problems on the system even  with load test applications that keeps the system on a constant heavy  load for testing purpose even when I over-clock the system (it is  normally not over-clocked, I just over-clocked it for stress tests to  rule out hardware problems). 

And memtest86 shows no errors.

So I don't think it is a hardware problem but I don't have Ubuntu load  test program.  I don't have any error logs as it seems the kernel panics  thus no log gets recorded. 

But I suspect it could be pulseaudio because it dumps error warnings in the logs

pulseaudio[1453]: lock-autospawn.c: Cannot access autospawn lock.
pulseaudio[1453]: main.c: Failed to acquire autospawn lock
pulseaudio[1764]: tagstruct.c: Assertion 'pa_proplist_get(p, k, &d,  &l) >= 0' failed at pulsecore/tagstruct.c:286, function  pa_tagstruct_put_proplist(). Aborting.

Other then that I have no clues on what is causing the freezes as the  freezes are so random, the system can stay up for days without freezing  then one day have one or two freezes shortly after reboot and the  session fully restored yet by the third time restoring the session it  never freezes again and can go days without problems. 

I have a Biostar A880G 
AMD X2 260
Mushkin Silverline 2x2GB DDR3 
Western Digital 1.5TB with Windows XP 64 taking a cluster adjusted partition for compatibility.

---

### Post by Psy02 on 2011-09-23
Any ideas? I just had a system freeze while the system was idle with firefox running with flash apps and mplayer yet everything paused and I walked away from the system.

Yet earlier I ran Phoronix Test Suite and had no problem even when I totally saturated the CPU, RAM and swap space.

---

### Post by LinuxFan999 on 2011-09-23
Do you Have the latest drivers? Is your system up to date?

---

### Post by Psy02 on 2011-09-23
> **LinuxFan999 said:**
> Do you Have the latest drivers? Is your system up to date?
I constantly run update manager and install all available updates.  My system is pretty stock so the drivers should be part of the normal packages as it is a ATI Radeon HD4250,  Realtek ALC662 (sound) and Realtek RTL8111DL (GbE).

---

### Post by Psy02 on 2011-09-23
Is anyone else getting pulse audio errors, here more pulse audio errors showing in my logs

pulseaudio[1558]: core-util.c: Home directory /etc/timidity not ours.
pulseaudio[1558]: lock-autospawn.c: Cannot access autospawn lock.
pulseaudio[1558]: main.c: Failed to acquire autospawn lock
pulseaudio[1860]: pid.c: Daemon already running.
pulseaudio[1808]: ratelimit.c: 13 events suppressed
pulseaudio[1622]: core-util.c: Home directory /etc/timidity not ours.
pulseaudio[1622]: lock-autospawn.c: Cannot access autospawn lock.
pulseaudio[1622]: main.c: Failed to acquire autospawn lock
pulseaudio[1917]: pid.c: Daemon already running.
pulseaudio[2390]: pid.c: Stale PID file, overwriting.
pulseaudio[2479]: pid.c: Daemon already running.
pulseaudio[2390]: ratelimit.c: 4 events suppressed


Maybe if I can clean up pulseaudio I won't get the freezes.

---

### Post by Psy02 on 2011-10-06
I'm still getting random freezes and it is to the point that Windows XP 64 is now my OS for doing serious work as it never crashes or freezes on me despite running on the exact same hardware no matter how hard I push it or how long I leave it running while Ubuntu 11.04 keeps freezing so I can rule out a hardware problem as Windows would have had issues too.

It is probably a diver issue but I don't know why more people experience it since my video card is a intergrated ATI Radeon HD4250, my soundcard is a integrated Realtek ALC662 and my network adapter is a integrated Realtek RTL8111DL so pretty standard hardware.

---

### Post by Kheops_74 on 2011-10-16
Any development? I install a fresh 11.10 version and have a lot of freezing. Look like it freeze when the CPU usage is high. If i watch a Flash video on Firefox (full screen) it freeze. Same with MythTV, i can watch TV but if an other process run as mythcommflag, it freeze. Last thing, each night between 1 o'clock and 4 o'oclock, it freeze again (with keyboard flashing).

I did a lot of testing but i'm not able to figure out the problem.

---

### Post by Kheops_74 on 2011-10-17
Yesterday, i disable mythcommflag and change the "permit queue job period" from 3 o'clock until 5 o'clock in the MythTV Backend. No freeze last night.

I understand that some job are very CPU intensive (mythcommflag, Flash full screen) but i don't understand why Ubuntu freeze instead of killing the job. Any thought on this?

---

