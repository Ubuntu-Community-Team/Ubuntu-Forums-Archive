---
title: "ubuntu won't startup please help!!!"
date: 2009-08-19
forum: General Help
---

### Post by shotgunn on 2009-08-19
Hello,

I have been using Ubuntu for about 4 months now.  It has been problem free, until now.  

When I start up the computer, it just keeps cycling, over and over again.

Startup...

Memory check, drive check, all that, 

Startup...

Occasionally it will show the Ubuntu logo with the orange progress bar.  Then it restarts.

I tried starting in recovery mode, to no avail.

I am now running the memtest.  I have no clue what this will do for me, if anything at all.

I use ubuntu for my CNC machine with EMC2 machine control software.

I have a VERY important project that requires this machine being up and running.

I am using a Shuttle KPC Intel Core 2 2.0Ghz, 500GB HD, 1GB RAM.

I have nothing of value on this computer other an EMC2 configuration file for my CNC machine.  All I need is one of two things...


1.  How can I get the machine running again, without losing the file?

or

2.  How can I extract the file safely.  Then I can re-install ubuntu which I would have no problem with.

If I mount my 500GB HDD (via usb to sata) to my Macbook Pro will I be able to access the files from my Mac?  If so I could just email myself the file and not have to completely reconfigure my CNC software (tedious, time consuming, and not really an option for me.

Please help, anyone.  Please.

Thanx,

shotgunn

---

### Post by jerrrys on 2009-08-19
no problem.  just use your install cd and choose option 'boot without install'.  navigate to your folder on hard drive and save to usb...

---

### Post by shotgunn on 2009-08-19
Since I made the original post, I have tried to boot from the install CD-ROM.  Even that won't work.  I don't see an option that says exactly 'boot without install'.  Although that sounds like the first option.  'Change nothing on my computer, etc...'  Which basically means boot OS form CD-ROM.

Any-hoo, It won't even let me do a fresh install.  I called getashuttle.com they said to try removing the RAM sticks and see if it will work with one or the other in each slot.  I am about to try this.

Any other suggestions are MORE than welcome AND appreciated!!!

Also, it has come to my attention that for the Mac there is a program called MacFUSE.  I have downloaded this, but it doesn't look like an application.  Does anyone know how to use this?  This should allow me to extract and save the one file I need from this machine.

Thanx,

shotgunn

---

### Post by e_james on 2009-08-19
From the symptoms you describe and a little of my own experiences, I think you have a hardware fault and I suggest that it is most likely the power supply or the motherboard. In the circumstances it seems you need to connect your hard drive to another working PC in order to retrieve your file. Any PC which can read a linux partition should do. This would include a Windows PC booted with the ubuntu CD. I can't speak for the Mac. This procedure should also eliminate the worst case possibility that the hard drive is faulty.

---

### Post by jerrrys on 2009-08-19
if you do a fresh install it will WIPE your files.  if you cant boot from cd (no installing required), and it still will not boot, then i think your computer has a problem.

---

### Post by shotgunn on 2009-08-19
Yeah man, I'm pretty certain that's what it is.  I think it may still be under warranty. I even tried another install disc.  Still no progress.  Tomorrow I am gonna try another processor and see where that takes me.

At one point just a few minutes ago I did get to the login screen, and put my username and password.  Then it took a dump.  It seems like a power failure.  Hopefully in the power supply and not somewhere in the motherboard.  I keep seeing this bright red LED near the CPU flashing.  

All I know is I have to get this machine running A.S.A.P.

Thanx,

shotgunn

---

### Post by shotgunn on 2009-08-19
Any other tips on how I can at least get that file from the hard drive?

---

### Post by e_james on 2009-08-20
I looked up that MacFuse utility and it certainly seems the right thing for the job, but I assume it's more complicated to use it than you would wish. It would definitely be too complicated for me. If I needed to do what you want to do, I would try to find a friend with a suitable PC and use that machine to retrieve the file. Is this not a viable option for you?

---

### Post by shotgunn on 2009-08-20
Well, it's not the processor.  I just bought a brand new Intel Dual Core 2.2Ghz.  I think it is the Motherboard or the Power supply....

When I press the power button the CPU fan starts, then stops, then starts, then stops, then it eventually tries to boot from the CD-ROM.  I still can't get to the actual ubuntu desktop or even boot from the CD-ROM.

I can only exchange the CPU for other store merch (bogus!!!)  They already told me they don't have the Shuttle K45 cases or the even the motherboard.

I think I might try going to Fry's...

Thanx,

shotgunn

---

### Post by e_james on 2009-08-21
It might be helpful to describe some of my own experiences.

I have several PCs. One of them, a standard tower case, began to restart unpredictably. At first I thought it was the fault of the DVD writer because it often happened as the disc started to spin, but then I thought about the sudden extra load on the power supply. I replaced the PSU and it has been running fine ever since.

I also have a Shuttle and the PSU fan got very noisy. I bought a spare fan and I also bought a new PSU from a spare parts supplier on the basis of make and model of the PSU. Mechanically, the new unit was a perfect fit but one of the cables needed to be extended.

---

### Post by running_rabbit07 on 2009-08-21
If you can get into BIOS, you can set the POST test from silent to long. And it will beep out codes if there is something wrong with your system.

---

### Post by shotgunn on 2009-08-21
My problem must have been either the Motherboard or the Power Supply.  I bought a new barebones case, put the CPU, RAM, and HDD in.  It started right up immediately.

$200 though.  I am gonna try and have the other one repaired under warranty service and hopefully sell it.

Thanx,

shotgunn

---

