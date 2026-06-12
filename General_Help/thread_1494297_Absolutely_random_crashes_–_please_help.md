---
title: "Absolutely random crashes – please help"
date: 2010-05-26
forum: General Help
---

### Post by El_Calavera on 2010-05-26
I have bought a new desktop computer last fall, and, after installing Ubuntu, was met with random freezes of the system. We are talking a complete freeze, cursor not moving, no reactions to sysrq-key, absolutely no reaction to anything, only a hard reboot would do the trick.
These freezes have happened occasionally since then, absolutely randomly, sometimes not for two weeks, sometimes several times per day. Also, the freezes leave no trace in any log file.
(The only suspicious comments i get from log files are
hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
and
pulseaudio[1365]: ratelimit.c: 860 events suppressed
but they seem to be common and I never found them mentioned in context with freezes like I experience.)

Very rarely, instead of a freeze, the system will just reboot all of a sudden as if i had pressed the reset button.
I have a parallel installation of WinXP for games, so far the freeze did not happen there.

I suspected an X crash and my ATI HD 4670 graphics card at first, tried another card, tried different drivers (radeon, radeonhg, fglrx), to no effect.
Since then I investigated a multitude of possible configurations:

[LIST]
[*]bios updates and different settings on my ASUS M4A785TD-V EVO. Especially disabling all kinds of processor features, like APIC, ACPI.
[*]ram test
[*]changed power supply (currently 500W beQuiet)
[*]changed hard drive
[*]changed dvd drive (mostly because Ubuntu disliked the first one)
[*]tried different kernels, from 2.6.31 to 2.6.34, also vanilla kernel
[/LIST]
Graphics card an processor temperatures are healthy, i.e. I have never witnessed more than 50°C, and that's with all cores on full load.

Everyone I know is at a loss, I have absolutely no idea what I should do now (I would not want to return the whole PC, I don't even know whether I can).
I have checked other posts on random crashes, but most turned out unrelated or did not arrive at any conclusion.

In any case, I would be grateful for any help to diagnose or even solve this problem. Thanks in advance.

---

### Post by TideMan on 2010-05-26
I had this problem a few years ago on one of my machines.
Turned out to be this:
[http://en.wikipedia.org/wiki/Capacitor_plague](http://en.wikipedia.org/wiki/Capacitor_plague)
When I looked closely at the mobo, I could see the fluid oozing out of the capacitors.
Replacement mobo fixed the problem.
I sold the old mobo on an Internet auction site, even though I clearly stated that its capacitors were leaking.

---

### Post by RTrev on 2010-05-26
You say, if I understand you correctly, that it hasn't done it yet under XP.. so far.  Maybe give it more time?  That might be a good test to see if we're looking at hardware issues.  Fire up XP and let it run for a while.

Have you looked through the logs (System | Administration | Log File Viewer) to see if you can find anything?

To be honest, I'm not sure which log to look in.. maybe someone else will have ideas on that.  I'd just browse them looking for any critical error messages.

You might also want to run the memtest from Grub, to see if maybe your RAM is doing something bad.

---

### Post by El_Calavera on 2010-05-27
@TideMan: Interesting, I've never heard of that. I'll give the Mainboard a closer look as soon as I can.

@RTrev: I had Windows running for up to 6 hrs at most, without anything ever happening. But then the freezes don't seem to correlate with uptime. Taking into account the frequency of freezes under Ubuntu, at least a few freezes should have happened under Windows by now.
I have searched all logs but there is absolutely nothing at the time the system freezes. There is the occasional "pulseaudio[####]: ratelimit.c: # events suppressed", but it doesn't seem to be connected.
I had run the memtest for 8 hrs without finding anything.

Thanks for the suggestions.

Ready to try any voodoo, I had also thought of installing the 32bit Ubuntu instead of 64bit. Does anyone know whether that's worth a try?

---

### Post by kokonobs on 2010-05-27
You should look at this thread. No solution but there is a lot of chat about it. And you could maybe add your voice to the launch pad bug report pages.

[http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)

---

