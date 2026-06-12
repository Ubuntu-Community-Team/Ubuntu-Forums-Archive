---
title: "SUSPEND TO RAM BROKEN with install of 9.10, WHY?"
date: 2010-03-16
forum: General Help
---

### Post by linuxalwaysbreakssuspend on 2010-03-16
First I would like to say that I am very tired of linux not working with suspend.  VERY TIRED.  This has been going on for a long time and it is apparently a curse that will just never completely go away. Never.  Five years from now linux will still have problems with suspend and the situation hardly improve.  What is so difficult about making suspend to ram work and keeping it working?

My last motherboard would not suspend at all in linux but fortunately or unfortunately, that board had a catastrophic failure one day and was replaced with a nice Gigabyte board that suspends very well-- when the OS is actually set up properly.

It worked great in 9.04 and I knew switching to 9.10 would be a mistake.  Unfortunately the speed improvements and more importantly the MEMORY FIXES (like when your system has been running for 72 hours and suddenly applications take minutes to launch or refresh despite your board running 8GB of ram) were too tempting to pass up on.  I upgraded two of my laptops and installed a fresh copy on my desktop and soon I noticed the difference between installing fresh and upgrading.

The laptops that had been UPGRADED suspended fine.  The desktop with the fresh install will skip suspend to ram and go right to the graphical password screen as if you had just completed a suspend-resume cycle.  In other words, if A is a running state, B is a suspended state, and C is a resumed state, ubuntu just skips B and goes right from A to C.  I have tried the graphical way of suspending and pm-suspend and neither work.  s2ram complains "s2ram_do: No such file or directory" when I try that.  Does ANYTHING work??  Stop breaking stuff already!

Potential reasons for this not working:
*Grub 2 -- old grub is still running on laptops because an upgrade does not switch grubs.
*Some ubuntu specific setting
*Nvidia Driver 185 (I don't have any other problems with it so perhaps not)
*Some grub/acpi boot setting
*who knows, this should just work!

The system is running the 64bit version of ubuntu with kernel 2.6.31-20-generic.  The kernel was just upgraded and the problem did not change so chances are it is not the kernel.

---

### Post by linuxalwaysbreakssuspend on 2010-03-17
Sorry if my first post came across rudely but does anyone have any input or advice?  This particular problem is absolutely infuriating because it keeps resurrecting.

---

### Post by dcstar on 2010-03-17
> **linuxalwaysbreakssuspend said:**
> Sorry if my first post came across rudely but does anyone have any input or advice?  This particular problem is absolutely infuriating because it keeps resurrecting.

What are the sizes of the swap files on the new systems?

---

### Post by linuxalwaysbreakssuspend on 2010-03-17
I'm not sure what you mean by new systems but the desktop with the problem has 8gb of ram and 2gb of swap.  I'm not using suspend to disk so this should not be important.  I am only concerned about suspend to ram.

The two laptops which do not have the problem each have a gigabyte of ram and about a gigabyte of swap.  One of the laptops is a 32 bit machine and the other is 64.

---

### Post by egalvan on 2010-03-17
> **linuxalwaysbreakssuspend said:**
> First I would like to say that I am very tired of **linux not working with suspend**.  VERY TIRED. .

To be more exact, it is **suspend not working with Linux**.

The BIOS-level code is *very* MS-centric...

As is the procedure to access information about the code and chip-level programming data.

Similar problems plague the video and wireless LAN side of things...


As long as too many Linux users are willing to suffer in silence, this will continue.

Fuming about it in forums does little good, sadly enough.

The only way to get a hardware vendor's attention is to write an actual, physical, *polite* letter,
 stating that you ***will not*** buy their product until it is supported *fully* under Linux, with Open Source Drivers.


The GNU/Linux/FOSS/OSS crowd is doing wonders within the limits placed on them by the marketplace.
They have my gratitude, and my financial support (via **donations**) whenever possible.

---

### Post by linuxalwaysbreakssuspend on 2010-03-17
The point is it WAS working in 9.04, but it isn't anymore.  What exactly was it that caused it to break?

---

### Post by j7%&lt;RmUg on 2010-03-17
Not sure what caused it to break for you but alot of my friends with laptops are saying that suspend is better in lucid.

---

### Post by dcstar on 2010-03-17
> **linuxalwaysbreakssuspend said:**
> I'm not sure what you mean by new systems but the desktop with the problem has 8gb of ram and 2gb of swap.  I'm not using suspend to disk so this should not be important.  I am only concerned about suspend to ram.

The two laptops which do not have the problem each have a gigabyte of ram and about a gigabyte of swap.  One of the laptops is a 32 bit machine and the other is 64.

So the working systems have Swap = RAM, and the non-working systems have Swap < RAM.

I reckon you might have a clue for a solution there..........

---

### Post by hanzomon4 on 2010-03-18
I'm having the same problem, it just started last week. I'd been suspending just fine before then

---

### Post by coldraven on 2010-03-18
I did a clean install of 9.10 64bit and let it choose how much swap it wanted.
So for 4GB RAM I got 6.1GB swap.
I have an integrated graphics card that uses 300MB of system memory.
It works fine although sometimes on resume the screen has dimmed and has to be turned back up, no big deal. (ATI problem!)
AFAIK swap has to be at least 10% BIGGER than your RAM.

---

### Post by egalvan on 2010-03-18
> **linuxalwaysbreakssuspend said:**
> The point is it WAS working in 9.04, but it isn't anymore.  What exactly was it that caused it to break?

You missed MY point...
which is that it's not **Linux's** fault that hardware is mostly designed and built to **work with Microsoft**,
and at times is specifically designed to break any other OS.

Place the blame where it belongs...

on the closed-source, NDA-ridden, proprietary hardware designers/manufacturers.

FOSS/OSS/GNU writers often have to jump through incredible hoops to reverse-engineer the drivers...

---

### Post by linuxalwaysbreakssuspend on 2010-03-20
At least two people on the thread looking for a solution, bo solution so far.
Any other ideas? It's not the swap size.

---

### Post by linuxalwaysbreakssuspend on 2010-03-20
Nobody knows anything?

---

### Post by ipsi on 2010-04-03
Dammit, I was really hoping someone had a solution for this - I have the exact same problem with a new laptop - suspend suspends for about a second (check pm-suspend.log), and that's pretty useless for a laptop I need to carry from work to home and back.

Hibernate doesn't work either.

I don't suppose you've found a solution yet?

---

### Post by linuxalwaysbreakssuspend on 2010-04-30
I ALMOST resolved it by removing a newly installed sata6 & usb3 combo card (U3S6 card from asus, the SATA side of things seems to cause trouble although my mobo's built-in SATA was never a problem).  However, although at that point I could ENTER suspend, I would be stuck with a blinking cursor (like so many other people) at resume.  I upgraded to 10.04 (from 9.10) thinking the problem would be fixed, but no, same issue.

I found that removing the module xhci before suspend will allow me to enter suspend!  On resume however, I get extreme graphical corruption and a complete lockup.  Perhaps removing the nvidia driver will also help.
--NOPE, same problem with generic Nouveau driver except without the graphical corruption (just black screen and total lockup, still can't even use Alt+SysRq-REISUB rebooting trick).  I'm going to try installing 10.04 onto a fresh partition (as opposed to my 10.04-upgraded system) to see if I can avoid this problem.  I'm close to getting it working, I can feel it.

---

### Post by linuxalwaysbreakssuspend on 2010-05-11
Well I set up a new partition to test an old 9.04 backup and I even updated it with the same Nvidia CUDA driver I was using in 10.04.  NO PROBLEMS WITH SUSPEND IN 9.04.  It boots a lot faster too.  Who spread the lie that lucid would improve boot speed??  

Interestingly, if I install 9.04 fresh I have some other sort of resume problem, but my updated backup of 9.04 works fine (running 2.6.28-14-generic).  There appears to be no end to the mystery!

In conclusion, I would say this is definitely another tick in Ubuntu's growing population of regressions, and that perhaps instead of changing the theme every 6 months or worrying about which side of the window the titlebar buttons should end up on, the developers should concentrate on fixing lingering bugs and regressions, especially with resume and suspend.

Windows starts with a 'W' because it frickin Works!
Ubuntu starts with a 'U' because it Used to work!  :mad:

---

### Post by linuxalwaysbreakssuspend on 2010-08-13
Just wanted to let the users here know that the problem is now solved by means of updates and updates alone.  Same machine has had recent ubuntu updates and an update to the newer 256.40 nvidia driver (cuda version) and sure enough, suspend now works great.  I can revert back to the old nvidia driver to test it but since the noveau driver gave me the same problem I suspect that the ubuntu updates were what (finally) fixed it.

Months of waiting and finally a fix.

END

---

