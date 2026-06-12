---
title: "Ubuntu 10.10 Freezes after start"
date: 2010-11-11
forum: General Help
---

### Post by DanDude on 2010-11-11
Hi!

I recently installed Maverick Meerkat on my laptop.
After a couple of days of use it started freezing after bootup.
Sometimes it takes 10 seconds and sometimes 10 minutes, it's completely random!
I have one application that starts on bootup wich is AWN.

Thank you!
Dan

---

### Post by azertyh on 2010-11-11
hello,
to find a possible reason of these freezes, look at the syslog or dmesg : in a terminal
```
tail -f /var/log/syslog
``````
dmesg
```

---

### Post by DanDude on 2010-11-14
What should I look for there? Will the syslog remember what has happened previous sessions?

---

### Post by azertyh on 2010-11-14
hello,
i'm not sure that syslog remembers previous sessions.
see these docs :
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)
[https://help.ubuntu.com/community/Troubleshooting](https://help.ubuntu.com/community/Troubleshooting)

there are also many threads about freezing ubuntu, do a search about it. perhaps one of them is related to your issue.

---

### Post by DanDude on 2010-11-14
For some reason, I no longer experience the problem...

Thanks for the effort!

---

### Post by DanDude on 2010-11-14
And now it has begun again, but this time it took like 1 1/2 hours before it freezed. After rebooting it freezed as soon as i opened Firefox, but it also happens at complete random! Really weird...

---

### Post by DanDude on 2010-11-15
I tried a couple of the things mentioned in the first doc, before my computer freezed again. I got nothing so far, no files indicated anything.

---

### Post by DanDude on 2010-11-19
Sorry for quadpost (:o) but could anyone help me?

---

### Post by b00nish on 2010-11-23
Hi

I experience the same problems since about 4 or 5 days. Before I had nothing like this.
It freezes about 30 seconds after LogIn, so that I have to do a reboot. After the reboot it usually worked fine for the day.

Since today it's that worse, that I'm now unable to use the system because it freezes after EVERY LogIn. I can reboot 10 times.. it alway freezes after LogIn. Funnily, I have changed nothing.

---

### Post by theSuperman on 2010-11-23
Can you hit Ctrl+Alt+F1 to enter a virtual terminal? What about ctrl+alt+backspace to restart X?

I had issues with running out of ram and having no swap space available. That caused X to lockup and I had to go into a virtual terminal to manually kill processes.

---

### Post by b00nish on 2010-11-23
No I can do neither of that.
Also I don't think that RAM should be a problem, since my machine has 4GB of it, which should be enough to boot up an OS as far as I know.

However maybe this issue is in my case related to another problem I have concerning NFS. (NFS locks up my machine when receiving big amounts of date.. and maybe some of my software does crawl trough my NFS shares after LogIn since recently.. don't know.)

---

### Post by DanDude on 2010-11-24
That would be weird in my case. Since I have only one Application running on bootup...

Edit: I can't use any of the commands either!

---

### Post by theSuperman on 2010-11-25
Ctrl+alt+F1 does not work? You can set up ssh on your machine and try and SSH into it.

---

### Post by gordintoronto on 2010-11-25
> **DanDude said:**
> Hi!

I recently installed Maverick Meerkat on my laptop.
After a cuple of days of use it started freezing after bootup.
Sometimes it takes 10 seconds and sometimes 10 minutes, it's completely random!
I have one application that starts on bootup wich is AWN.

Thank you!
Dan

It's related to your hardware. Please describe it! CPU, memory, video card, network connection. Is it a dual-boot system ,and if so, does the other OS also freeze?

---

### Post by DanDude on 2010-11-26
Memory: 1001.5MiB
Processor: Intel Pentium 1.70GHz
CPU MHz: 1694.307
VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
It's not a dual boot.

---

### Post by DanDude on 2010-11-27
I tried to turn off effects, it has seemed to help! I'll give you some feedback later.

---

### Post by spiritofjerry on 2010-12-28
I am also experiencing the same issue, and am trying to determine if it is a hardware or software problem (I'm leaning toward software).  The Xubuntu 10.10 OS freezes (so far, only 2 instances) occur while performing tasks like installing packages from Synaptic or transferring files between two external hard drives.  I am running Xubuntu 10.10 on:

eMachines EL 1200-06w
NVIDIA® GeForce® 6150SE integrated video
1 GB DDR2 RAM
4 GB Swap Partition

After the freeze occurs and I do a hard reboot, the GRUB is always fine, and I can always boot back into the OS without a hitch.

I also have Windows XP installed on it's own separate partition, and the freezes have never occurred in Windows, nor has my ability been compromised to boot into Windows after one of these random Meerkat freezes. I do use Windows less often, but I do perform more memory intensive tasks like playing games Freelancer or Fifa '03, or running Traktor DJ Pro. This makes me believe the RAM itself is fine (and I've tested it for integrity, just to be sure).

If you have any recommendations on how to go about debugging this issue, please do share your comments before I do some major harm to my system.  I do believe this is a completely resolvable issue - and my guess the issue is either a memory or video issue with stemming from a 10.10 driver incompatibility with my software, or a RAM overload, or maybe even a bad sector on the hard drive?  My immediate objective is to continue using Meerkat until the freeze happens again, then I will try restarting X or killing processes from a terminal (if possible).

*Another side note, I owned an older model (circa 2002-2003) Compaq Presario desktop computer with an intel chipset/integrated graphics (64MB shared) that would freeze all the time with the xorg driver released in version 9.04, forcing me to revert back to the older xorg driver to make my chipset compatible with 9.04.  Ubuntu froze much more often with that setup than it does on my current setup, but I am slightly tempted to believe this could be another scenario of the same kind.

---

