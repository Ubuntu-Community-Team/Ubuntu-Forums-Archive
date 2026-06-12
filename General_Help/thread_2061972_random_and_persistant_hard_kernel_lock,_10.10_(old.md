---
title: "random and persistant hard kernel lock, 10.10 (old and newer kernel) and 12.04 (live"
date: 2012-09-23
forum: General Help
---

### Post by dave.kts on 2012-09-23
Seriously dissapointed, I dont know where to begin troubleshooting here. Getting hard lockups at random times, doing anything from web browsing to copying files to a thumb drive, just listening to music, I was even installing 12.04 Ubuntu Studio and it locked up on me during the install. (I am having an issue with anything 12.04 now, when I'm done installing and on first boot Im greeted with the "Your running on low graphics mode" wether I boot and install the live CD with "nomodeset" or not)

32 or 64 bit makes no difference. My old standby OS is super Ubuntu 10.10 32 bit. I dont remember having this problem with it until maybe a year ago with a kernel update and started getting hangs. Booted from old kernel, no issue. Now, it doesnt matter which kernel i boot.
I tried several newer distro's including solusOS 1.1 (got screwed up after an updated NvIdia driver or something), Ubuntu Studio 12.04 (kernel lockup near the end of the install) AVlinux (dont know if it would have locked up, never installed graphics correctly) and regular Ubuntu 12.04 64 bit, which would lock up running the live CD.

I was running solusOS for some time and dont remember any lockups at all with that. it just got messed up after a series of updates, and instead of trying to fix it i just started trying new distros. SolusOS 1.2 on the other hand had locked up on me tho shortly after install.
 I was impressed by the firewire latency with my presonus audio interface with solusOS so I thought I'd try some multimedia distros.

one thing to mention, I almost always have my android phone plugged in and tether internet to this computer. I dont think its that tho, its been great on several computers of mine and no issues but here on this one.

When it happens I have no keyboard or mouse control, caps lock non functional, all video freezes but no distortion, audio that is playing plays a 1 or 2 second never ending seamless loop.

Hardware:
Intel DP43BF board, no on board vid
Q8300 core2 quad
4 GB Gskill ram, underclocked (bought it for faster MB that failed in 3 months)- memtested overnight, twice, no errors
PNY Nvidia quaddroFX550
2 SATA hard drives, Intel SSD, 2 DVD roms
stable, oversized 80Plus power supply
atheros wifi PCI, not being used but installed

This board requires a "pci=assign-busses" boot parameter. I thought once that a "nomodeset" parameter was needed for this board but i could be mistaken. Lockups happen either way.

I really want to smash this thing. Should I just smash it to little pieces? Hell I can't even enjoy videos without tearing or compiz effects without crashing any 3D program. XFCE= no tearing, but to me its ugly.
Enlighten me: why did Intel support warn me that this MB does not support linux??

any advice short of a geek hooking up to it via serial console and waiting for it to happen again?

---

### Post by dave.kts on 2012-09-26
hump day bump day

---

### Post by Rexilion on 2012-09-27
Ubuntu 12.04 LTS is using the 3.2 kernel, try upgrading to the newest kernel. Might fix your regression. Is there any change you can get us a dmesg when it hangs?

Furthermore, what video card do you have? If you install the proprietary drivers (if available), do the lookups occur as well? Do you know since what kernel version you experience this?

We could try a bisect if it's correctly reproducible...

---

### Post by dave.kts on 2012-09-27
As for using 12.04- I cant yet until I figure out how to get past "configure your graphics manually" screen (no GUI) after a fresh install. Never had to do this untill 12.04.

Not sure what specifically you want for dmesg, how far back does it save these if they are of use? Let me know what you want to see or what I should be doing to prepare for the next lockup.

My video card is a PNY Nvidia quaddroFX 550 and this has happened using both the Nouveau drivers and the proprietary drivers, My 10.10 system is using version 260.19.06 and the kernel will hang, and I've recently had SolusOS 1.2 installed with the most current Nvidia driver, and it locked up, as well as the live installer of Ubuntu studio, during install, using non-proprietary. I have heard of others having lockups using Nvidia cards with nouveau drivers, and there is a boot parameter that can fix that (havent tried it)

My 10.10 system is booting with 2.6.35.32 generic pae and have 2 other kernels available, has locked up using any of those. And whatever kernel version the 12.04 image has, locks up with that too. Sorry I cant be more specific on when this started happening, it may have always happened on this PC but thought it was something else, I had thought that "nomodeset" had cleared it up at one point, but doesnt help anymore, or never helped it to begin with (I just wasnt having any issues for awhile)

Im afraid its not reproducible, i can go days or weeks with no trouble, then next time i wake it, or boot it, it will hang- 5 min into a session, or maybe 2 hours.

If its worth mentioning, an XMBC session will lock on this as well.

One more thing (in 10.10 only), I have a quad core and sometimes ill have a constant 25+% CPU use even tho sys monitor does not show the culprit of the use. It speads itself out over all of the cores, but will remain at 25-28% CPU use forever until I suspend or reboot. System doesnt seem any slower because of this, but happens frequently, randomly, and seems unrelated to predicting a kernel hang.

---

### Post by Rexilion on 2012-09-28
Well that narrows it down to a regression between 2.6.35 and 2.6.36 which is a really good start. It seems to be CPU related.

If the machine locks-up, press (while waiting 5 seconds between each one):

SYSRQ+R
SYSRQ+E
SYSRQ+I
SYSRQ+S
SYSRQ+U
SYSRQ+B

Maybe that might save the logs. On next boot, check /var/log/dmesg* for errors/oops/bugs/warn etc.

---

### Post by dave.kts on 2012-09-28
In dmesg I do get these warnings, and I see that ACPI may cause lockups in some systems... I've never tried disabling it
ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20100428/tbfadt-369)
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0xDF624F40/0x00000000DF625E40, using 32 (20100428/tbfadt-486)

---

### Post by Rexilion on 2012-09-29
Try disabling ACPI then, that could help bisecting it to a specific region of the kernel.

---

### Post by dave.kts on 2012-09-29
Just locked again, tried your REISUB suggestion, dont think it logged anything. On next boot I added acpi=off, and also changed BIOS to S1 sleep state as opposed to S3.
Now I see in dmesg several times:
broken BIOS!!

will wait and see if I have another lockup. may be awhile, worked for 5 days in between lockups this time..


[https://dl.dropbox.com/u/24530033/logs%20sept%2029/dmesg](https://dl.dropbox.com/u/24530033/logs%20sept%2029/dmesg)
[https://dl.dropbox.com/u/24530033/logs%20sept%2029/dmesg.0](https://dl.dropbox.com/u/24530033/logs%20sept%2029/dmesg.0)

---

### Post by dave.kts on 2012-09-29
Ohhhhhh... so basically I have no sleep function with acpi=off??
unacceptable solution.. if that "fixes" the hangs. Also won't hibernate, all I get is this screenshot, and never shuts down:

[https://dl.dropbox.com/u/24530033/logs%20sept%2029/0929121035.jpg](https://dl.dropbox.com/u/24530033/logs%20sept%2029/0929121035.jpg)

---

### Post by Rexilion on 2012-09-30
Can you do, while acpi=off:

```
cat /sys/power/disk
```

And post the output here?

---

### Post by T.J. on 2012-09-30
I realise this might be vague and useless, but I used to have similar trouble and it turned out to be the CPU governor daemon locking up the system at random intervals.  I don't use the current version of Ubuntu (went back to Debian), so I can't give you specific instructions, but if the governor daemon is the cause, you can disable it and hopefully keep your other ACPI features.

---

### Post by dave.kts on 2012-09-30
> **Rexilion said:**
> Can you do, while acpi=off:

```
cat /sys/power/disk
```And post the output here?

with that all I get is :
david@SuperU:~$ cat /sys/power/disk
test testproc [shutdown] reboot 
david@SuperU:~$

and nothing happens.

---

### Post by Rexilion on 2012-09-30
No, just checking if it was still on platform. But that is not possible if you have acpi disabled (heh..).

Start bisecting then?

---

### Post by dave.kts on 2012-09-30
should I first start with BIOS settings, since I saw warnings about BIOS? maybe turn off processor power management in BIOS?
Or try to disable the cpu governor daemon like T.J. suggests? I was looking at threads pertaining to that and I saw a comment by a poster that his core2 quad Q9300 (close in specs to mine, just larger cache) does not work correctly with the governor daemon. He didnt mention having lockups tho.
I dont know what to bisect here, I'm a dummy :)

---

### Post by Rexilion on 2012-10-01
Sweet, we'll try disabling cpufreq then, can you post me the output of:

```
lsmod
```

---

### Post by dave.kts on 2012-10-01
https://dl.dropbox.com/u/24530033/logs%20sept%2029/lsmod

---

### Post by Rexilion on 2012-10-02
I don't see a cpufreq driver loaded. Could you post the output of:

```
find /sys -iname \*cpu\*
```

---

### Post by dave.kts on 2012-10-02
> **Rexilion said:**
> I don't see a cpufreq driver loaded. Could you post the output of:

```
find /sys -iname \*cpu\*
```

here are 2, 1 with processor power management off in BIOS, the other with it on.
[https://dl.dropbox.com/u/24530033/logs%20sept%2029/-inamecpu_BIOS_cpu_powersave_off](https://dl.dropbox.com/u/24530033/logs%20sept%2029/-inamecpu_BIOS_cpu_powersave_off)
[https://dl.dropbox.com/u/24530033/logs%20sept%2029/-inamecpu_BIOS_cpu_powersave_on](https://dl.dropbox.com/u/24530033/logs%20sept%2029/-inamecpu_BIOS_cpu_powersave_on)

I've had it turned off for a day or 2 now, no lockups so far (too early to tell)- CPU doesnt throttle down, but i dont care, this CPU runs cool and quiet, fan runs at 600 RPM all day and I run low 30 temps. only throttles down to 2GHZ (from 2.5) when enabled. Preserves the sleep function so if it works- good, but for the sake of it being solved, I feel the solution isn't an acceptable "fix"- having to disable it in BIOS.. for those that dual boot.. would rather fix or disable it in linux

BTW thank you for your time Rex

---

### Post by Rexilion on 2012-10-03
> **dave.kts said:**
> here are 2, 1 with processor power management off in BIOS, the other with it on.
[https://dl.dropbox.com/u/24530033/logs%20sept%2029/-inamecpu_BIOS_cpu_powersave_off](https://dl.dropbox.com/u/24530033/logs%20sept%2029/-inamecpu_BIOS_cpu_powersave_off)
[https://dl.dropbox.com/u/24530033/logs%20sept%2029/-inamecpu_BIOS_cpu_powersave_on](https://dl.dropbox.com/u/24530033/logs%20sept%2029/-inamecpu_BIOS_cpu_powersave_on)

I see that it loads two drivers:

- X86_CPUFREQ_NFORCE2
- X86_ACPI_CPUFREQ

But I do now know which one is eventually used. It is being used, but in my case there is a file called 'scaling_driver' inside these cpufreq directory's which says: powernow-k8.

I also think you posted the output of:

```
lsmod
```

with scaling disabled inside the BIOS (am I correct?). If you want to know which driver you are using, you have to provide the output of (with sudo):

```
dmesg
lsmod
```

_However, for now, disabling this inside the BIOS is a pretty good solution since you are now absolutely sure it's disabled. I would say, test it out for a few weeks. If it doesn't hang anymore then you know it's in cpufreq, if it does then we have to look further._

If it's in cpufreq, then we can look inside the kernel directory for commits to test/revert (which is a relatively small task since you narrowed it down to cpufreq).

> **dave.kts said:**
> I've had it turned off for a day or 2 now, no lockups so far (too early to tell)- CPU doesnt throttle down, but i dont care, this CPU runs cool and quiet, fan runs at 600 RPM all day and I run low 30 temps. only throttles down to 2GHZ (from 2.5) when enabled. Preserves the sleep function so if it works- good, but for the sake of it being solved, I feel the solution isn't an acceptable "fix"- having to disable it in BIOS.. for those that dual boot.. would rather fix or disable it in linux

The fact that it scales from 2,5GHZ to 2GHZ makes me think there is something wrong indeed (with cpufreq). My CPU's all scale till at least half of their max processing power. But I'm not sure though...

> **dave.kts said:**
> BTW thank you for your time Rex

No problem!

---

### Post by dave.kts on 2012-10-04
did you want me to post those outputs with CPU scaling on or off in BIOS?

yeah I thought it was abnormal to only scale down to 2.0 GHZ- when the P4 3.2 that I used to cook eggs on.. er I mean use in this motherboard would scale down to 1.8 or so,  my celeron laptop scales down to 600 MHZ.. im not sure tho. Cant say I know what windows xp shows with this CPU, i try not to use it. should i fire it up in XP?

---

### Post by dave.kts on 2012-10-04
[https://dl.dropbox.com/u/24530033/logs%20sept%2029/dmesg_10_4_2012](https://dl.dropbox.com/u/24530033/logs%20sept%2029/dmesg_10_4_2012)
[https://dl.dropbox.com/u/24530033/logs%20sept%2029/lsmod_10_04_2012](https://dl.dropbox.com/u/24530033/logs%20sept%2029/lsmod_10_04_2012)

these are with scaling enabled in BIOS. I assume you want sudo dmesg and sudo lsmod?
the terminal seemed to not capture all of the dmesg output

---

### Post by Rexilion on 2012-10-04
> **dave.kts said:**
> [https://dl.dropbox.com/u/24530033/logs%20sept%2029/dmesg_10_4_2012](https://dl.dropbox.com/u/24530033/logs%20sept%2029/dmesg_10_4_2012)
[https://dl.dropbox.com/u/24530033/logs%20sept%2029/lsmod_10_04_2012](https://dl.dropbox.com/u/24530033/logs%20sept%2029/lsmod_10_04_2012)

these are with scaling enabled in BIOS. I assume you want sudo dmesg and sudo lsmod?
the terminal seemed to not capture all of the dmesg output

Then I guess it would be the ACPI cpufreq driver. The dmesg you provided is indicating that it's not nForce2 (it could have made an error!).

This would give a very strong indication that you are using the generic driver which uses ACPI. That certainly makes some alarmbells ring since ACPI is known for it's diverse amount of 'implementations'.

Yes, I really think you should test with cpufreq disabled inside your BIOS. Test it for 2 or 3 weeks, if the hangs are gone then we could look at bisecting it. Or I could give you steps to disable cpufreq using kernel compilation. This would allow you to use cpufreq under Windows, while avoiding it under Linux. That would be a suitable workaround.

Even better would be to start bisecting, I looked at the amount of commits that were made to the acpi cpufreq driver between .35 and .36, there were only ten. Assuming that the occurence of you switching cpufreq driver between .35 and .36 has not occurred. And assuming that .36 allowed you to use cpufreq for this first time has not occurred.

---

### Post by dave.kts on 2012-10-04
> **Rexilion said:**
> Even better would be to start bisecting, I looked at the amount of commits that were made to the acpi cpufreq driver between .35 and .36, there were only ten. Assuming that the occurence of you switching cpufreq driver between .35 and .36 has not occurred. And assuming that .36 allowed you to use cpufreq for this first time has not occurred.

I'm not sure I'm following.. could you clarify about the amount of commits..... between .35 and .36?  If you are refering to kernel 2.6.35 vs. .36 then I may have given incorrect information, sorry. These are my currently installed 10.10 kernels:

david@SuperU:~$ dpkg --list | grep linux-image
ii  linux-image-2.6.35-28-generic-pae     2.6.35-28.50                                      Linux kernel image for version 2.6.35 on x86
ii  linux-image-2.6.35-30-generic-pae     2.6.35-30.61                                      Linux kernel image for version 2.6.35 on x86
ii  linux-image-2.6.35-32-generic-pae     2.6.35-32.67                                      Linux kernel image for version 2.6.35 on x86
ii  linux-image-generic-pae               2.6.35.32.42                                      Generic Linux kernel image

but keep in mind that lockups occured on 12.04 live installer CD, and other distros. This may have been a problem I've had ever since I've had this board. It replaced an AsRock board that all of the USB hub failed on, which replaced a board that the SATA controller failed on... 2 power suplies..3 HD's... winXP failed... new install: cloning failed... all while trying to make a demo for the band.

I'm going salmon fishing this weekend so ill check back in monday. ill keep running it with scaling turned off in BIOS. but I will want to get to the bottom of this if we can. Thanks again

---

### Post by Rexilion on 2012-10-05
Let me get this straight, from your observations I conclude the following:

- 2.6.35 works, no lockups
- above 2.6.35, lockups

A prime suspect in these lock-ups is the cpufreq driver which you just disabled in the BIOS. To narrow it down, disable cpufreq in the BIOS and boot a kernel that previously caused lock-ups.

Between 2.6.35 and 2.6.36 there were about 10 patches inside the cpufreq infrastructure and drivers.

Furthermore, I quote:

>  One more thing (in 10.10 only), I have a quad core and sometimes ill have a constant 25+% CPU use even tho sys monitor does not show the culprit of the use. It speads itself out over all of the cores, but will remain at 25-28% CPU use forever until I suspend or reboot. System doesnt seem any slower because of this, but happens frequently, randomly, and seems unrelated to predicting a kernel hang. 

To me, this also points to some cpu problem. Especially since it's 'fixed' after a reboot/resume/thaw. Since the kernel reïnitialises the CPU and freshly applies cpufreq on top of it.

The fact that it seems unrelated doesn't mean it's relevant. It could be a race condition that occurs based on probability (which is also a bug btw).

So, for now (and I assume you already did that before you went fishing) is that you have booted a Linux OS with a kernel version above 2.6.35 and have CPU frequency scaling disabled in the kernel.

When you get back, check for both symptoms:

- ghost cpu usage 25%
- hard lock-up

Hope they bite!

---

### Post by dave.kts on 2012-10-08
Incorrect sir, as for the .35 vs. .36 I only have 3 updates of .35 installed, have never had any .36 installed on 10.10 as i left this as a backup system a while ago to try other distros. (and now updating is broken.. more details to follow)
I don't think there was a point that the lockups started happening in relation to kernel version, I think I had just initially blamed it on it because I hadnt noticed it happen until after one of the later kernels were installed. I had thought that booting with an earlier kernel would prevent the lockups but that wasnt the case, I still have lockups on my earliest version.
So long story short, It seems to have nothing to do with the kernel version.

As for the ghost process, I found it to be "apt-get" using TOP, and would stay at 100% (of 1 core) forever untill I would sudo kill the PID. after 10-15 seconds of heavy HD activity, the process would die and everything seemed fine, CPU usage back to normal. Something to do with CRON hourly, or daily, I have no idea what any of it is doing but I know that whenever I try to use an apt-get install command I get an error like: E: Unable to locate package bla/bla/bla or unable to lock something something..
Not concerned with fixing this because it is only an issue in 10.10 and as soon as we figure out the lockup issue, I'm going to get the 12.04 to work with my video and not worry about the 10.10

So far no lockups with scaling disabled in BIOS...

---

### Post by dave.kts on 2012-10-10
Fail.
just locked up with scaling in BIOS disabled.
watching youtube, nothing else going on. everything froze and audio loops. next boot BIOS takes ~20 sec. longer to post.

---

### Post by mardybear on 2012-10-10
hi dave.kts

I'm no expert and i don't want to sidetrack your troubleshooting but it seems like a hardware issue to me. Random locks are typically more a hardware than a software issue. The problem may be more than just your BIOS settings.

I believe you mentioned running windowsXP in an earlier post. This is something i would certainly try to determine whether it's a linux or in fact a hardware issue. If windowsXP also causes problems then at least you know it's a hardware issue.

Good luck,

Mardybear

---

### Post by dave.kts on 2012-10-10
Doesnt hang in XP, altho i did have some hardware compatability/ driver issues that would cause BSOD.
also worth noting that I used to use an M-audio Delta 1010lt PCI card in this, until I did a BIOS update and after that BIOS wouldnt even post with that card anymore. (I changed over to a firewire audio interface )
 Pretty sure all that is straightened out tho, but I havent used XP in months upon months. I use XP for music production, so it does not see internet. Now I'm not working on any projects, so I use Linux on it (and my laptop). 

I think I'm going to take this intel board out and pick off the capacitors one by one with my rifle this weekend. Thats what I call troubleshooting.

---

### Post by mardybear on 2012-10-10
You mentioned a history of issues (ie. soundcard, black screen, query resolved) but haven't used windowsXP much lately. If it were my system, i would boot to windowsXP and run it solid for a couple days....complete all the windows updates, reboot as necessary, tax the system with your music software/whatever...and see if it's stable or also gives you random freezes or black screens. If still a problem then it's probably time to get your rifle loaded :)

Take care,

Mardybear

---

### Post by dave.kts on 2012-10-13
I'm still wondering why I didnt have any lockups when I was running SolusOS 1.1 and yet tried 1.2 (and many others) and did have a lockup.
I won't test in XP because I know the hardware works with SolusOS 1.1 and I dont want that OS using internet, which is mostly what I'm using this for right now. It already has virus issues.  XP is just too vulnerable using internet, and too risky on a DAW
Your probably wondering why I dont just use SolusOS if it works. Well I want a "studio" distro to work with since I discovered how low of a latency is possible with my firewire audio box. SolusOS 1.1 used some custom kernel that wasn't RT but I still had great performance.

---

### Post by mardybear on 2012-10-13
hi dave.kts.

Since this is an Ubuntu forum, just for the record i prefer Linux over Microsoft products and am a happy longtime Ubuntu user :)

I run several computers on a business network, three of which still use WindowsXP on the internet on a daily basis with no problems or security concerns. Microsoft still provides monthly security updates and has commited to ongoing critical update support until April 2014.

Sounds like you have a triple boot computer but not a single operating system allows you to fully complete your work, plus you had a partially unsuccessful BIOS update:
WindowsXP has virus problems
SolusOS 1.2 doesn't work properly
Ubuntu has a problem with random lock-ups

Since you're reluctant to run WindowsXP, why not boot and run your system from a Linux live CD for a few days to see if you still expereince random lock-ups (eg. Ubuntu liveCD, Puppy Linux).

If still random lock-ups then you probably have a hardware issue. Either run the appropriate software to test your hardware (eg. ram test, hard drive scans, etc) or replace/upgrade your system or specific components. Windows and Linux have good tools to test your ram and hard drives...not sure if you've recently tested your hardware?

If no random lock-ups then just your operating system installs aren't working properly. In this case, you might consider reformating your hard drives and installing fresh operating systems. For me a fresh install is always a last resort but in this case it may be warranted. I'm presently using an Ubuntu install that's >5 years old and it works great every day.

Just my thoughts. Your system you decide but it does not sound like you are very happy with it's present performance anyways.

In regards to your SolusOS upgrade comment, it is possible your system may have developed a hardware problem around the same time you attempted to upgrade to SolusOS 1.2.

mardybear

---

### Post by Rexilion on 2012-10-14
> **dave.kts said:**
> I'm still wondering why I didnt have any lockups when I was running SolusOS 1.1.

SolusOS uses a 3.3.6 kernel with BFS and preempt.

Preempt is bad for latency, and BFS might cover up your 'bugs'.

I also see things mentioning Optimus which also indicates a recent Xorg server (and co?).

That's a clue...

---

### Post by dave.kts on 2012-10-14
> Sounds like you have a triple boot computer but not a single operating  system allows you to fully complete your work, plus you had a partially  unsuccessful BIOS update:
WindowsXP has virus problems
SolusOS 1.2 doesn't work properly
Ubuntu has a problem with random lock-ups
-yes, except I have a non-working (low graphics mode only) DreamLinux installed rather than SolusOS 1.2. I'm pretty sure I had a lockup running solusOS 1.2 from live CD

> Since you're reluctant to run WindowsXP, why not boot and run your  system from a Linux live CD for a few days to see if you still  expereince random lock-ups (eg. Ubuntu liveCD, Puppy Linux).
-been there, done that, I think it was solusOS 1.2 that locked up on live CD, and installation from live CD failed with Ubuntu Studio 12.04

> If still random lock-ups then you probably have a hardware issue. Either  run the appropriate software to test your hardware (eg. ram test, hard  drive scans, etc) or replace/upgrade your system or specific components.  Windows and Linux have good tools to test your ram and hard  drives...not sure if you've recently tested your hardware?
-ran memtest extensively, and I always view and refresh SMART data for my 3 drives, all are rather new and trusted brands, not a single bad sector anywhere. Have ran disk utilities.

> In regards to your SolusOS upgrade comment, it is possible your system  may have developed a hardware problem around the same time you attempted  to upgrade to SolusOS 1.2.
-I was experiencing lockups in 10.10 before I installed SolusOS 1.1, didnt seem to have any trouble while using 1.1 (but a series of updates crashed the Nvidia drivers) so at that point I was determined to get a Linux based production distro installed, and discovered that all these other distros were experiencing lockups as well.
as for XP all I have to do is reinstall from a saved image, and run 4 days of updates (sucks because I tether from android phone and windows updates run terribly slow thru it) I will have to do that when I'm ready to use it for an audio workstation again, but as a rule of thumb you should never use internet on an audio workstation.
Ideally I want to make the transition to linux fully and use free software for the audio production because I cant afford the "real stuff" written for microsoft and run into stability problems going the route of hacked, downloaded software. Hence the virus, software crashing and losing work.. and to be honest I see beter latency performance in linux.

---

### Post by mardybear on 2012-10-14
howdy dave.kts.

If you were getting lock-ups with a liveCD then something is terribly wrong. You mentioned NVidia graphics card. Lots of linux users have had a lot of challenges running Nvidia graphics.

Just a hunch but you may want to take a look at your graphic drivers. I'm sure there's lots of info on this forum about Nvidia graphic card installs/solutions.

Alternatively you could swap out with another non-Nvidia graphic card to see if this fixes your problem (this might be the easiest/quickest solution).

Only other solution i can think of off-hand is to reinstall SolusOS 1.1 and avoid updates, as this install seemed to work best for you, but this is hardly the most desirable outcome and might not let you setup your ideal Linux audio system.

mardybear

---

### Post by dave.kts on 2012-10-23
i wish i had another video card around to test but i dont.  do you think it is more likely to be my video card,  or my wireless card,  or even the android phone?  I doubt it is the phone. I'm wondering if maybe I should just buy a pcmcia serial card for my laptop. would i be able to get some answers from that?

---

### Post by mardybear on 2012-10-24
> **dave.kts said:**
> do you think it is more likely to be my video card,  or my wireless card,  or even the android phone?
Hi again...

There's no way for me to know for sure...maybe someone else on the forum has some better ideas. If it was my system i would systematically try to rule out hardware issues. Try running your Ubuntu install for a while using a wired connection instead of wireless and see if it freezes at all over a few days. Once an Ubuntu install is set up and running well it should be able to run for days with hardly a hiccup.

Me still thinks it's likely your graphic chip. Have you tried different Nvidia drivers in Ubuntu? One thing i've never had to try myself but may be helpful is to select 'recovery mode' from the grub menu when you boot your system. Then select the failsafeX option (failsafe graphic mode). Next option choice would be to try running your system in 'low graphic' mode for a while to see how it responds. If this doesn't work, then reboot and select the 'reconfigure graphics' option and see if this helps you get things figured out.

Get back to the group when you've had a chance to trial, as others may be able to provide more advice.

mardybear

---

