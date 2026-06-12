---
title: "Strange hardware issues"
date: 2010-11-24
forum: General Help
---

### Post by sydbat on 2010-11-24
I built a box for a client. Nice one too...however...

I was checking out why the sound 'skips' while he listens to music, or watching videos. I upgraded alsa to 1.0.23 and this seemed to help. After this upgrade, and the subsequent reboot, Update Manager popped up with a new kernel. I installed it. I rebooted. 

When the post screens finished, the system had "booting operating system now' (or something very similar) at the top of the screen, then the screen went blank and the box rebooted.

After checking everything in the bios, and popping in a LiveCD (10.04), I found that I could access the hdd, but it would not boot at all. Sometimes it would not be recognized by the motherboard at all. Also, I tried reinstalling grub, but the error was very weird...something like wrong partition scheme (I will have to try this again and post the results here).

At first, I thought that the hdd had decided to die. I have brought the drive to my workshop and plugged it into a known good box (from which I am typing). The same results - no booting, but on this box, the drive is not recognized by the motherboard. I have been able to make the necessary backups for my client because I can mount the drive fine in Ubuntu.

So, is it a hardware issue (bad hdd)? Or did the kernel update yesterday (Nov 23 2010) bork the / partition in some way?

System specs for client box:
Gigabyte ga-890xa-ud3_e 
AMD Phenom II 6 core
8GB RAM
NVidia GT220 1GB
Seagate 2TB Barracuda XT SATA III w/ NCQ, 64MB Cache (this is the 3rd one in 3 months)

If you need more info, please ask.

---

### Post by sydbat on 2010-11-25
A bump.

Another question - is there some / file that needs to be removed or updated to make the drive bootable again? (obviously depends on the drive being in good physical shape and recognized by the BIOS)

---

### Post by sikander3786 on 2010-11-25
> The same results - no booting, but on this box, the drive is not recognized by the motherboard.

At least, it should be recognized. If not, I would say it is some hardware problem.

> is there some / file that needs to be removed or updated to make the drive bootable again?

Bootinfoscript would tell us about that. Please follow the instructions here and post the output.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Don't forget to wrap your output with code tags ;-)

But you'll need to plugin your HDD to some motherboard that recognizes it.

How did you mount it under Ubuntu? It is not being recognized in the Bios but can be mounted in the OS?

---

### Post by sydbat on 2010-11-25
> **sikander3786 said:**
> Bootinfoscript would tell us about that. Please follow the instructions here and post the output.

[**http://bootinfoscript.sourceforge.net**](**http://bootinfoscript.sourceforge.net**)Fixed your link...you forgot the 'u', which brings you to a very bad place.:D

> But you'll need to plugin your HDD to some motherboard that recognizes it.

How did you mount it under Ubuntu? It is not being recognized in the Bios but can be mounted in the OS?As for the BIOS thingy, I find it strange too. Might be a total hardware issue. I'll download the script, find a mother to put the drive on (that recognizes it) and post the info shortly.

---

### Post by gordintoronto on 2010-11-25
My vote: it's a bad HDD.

If you look at the user ratings on newegg, all the "large" hard drives have abysmal ratings. I'm running a WD "black" 640 GB drive, which has a much better rating than all the larger drives. (Oops, Samsung has some highly rated large drives.)

---

### Post by sydbat on 2010-11-26
Update - Not a bad HDD. Somehow, / kept coming up as 'not recognized', while /home was fine. I just reinstalled 10.04 without issue.

Also, the HDD shows up consistently on other motherboards I have plugged it into, except for the client's. I'll be replacing that mother and his power supply.

Thanks for your help!

---

