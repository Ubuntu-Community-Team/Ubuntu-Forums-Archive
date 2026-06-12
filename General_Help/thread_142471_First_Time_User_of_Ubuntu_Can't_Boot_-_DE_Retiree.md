---
title: "First Time User of Ubuntu Can't Boot - DE Retiree"
date: 2006-03-10
forum: General Help
---

### Post by DE Retiree on 2006-03-10
I am a complete novice with Linux.  Ran the "live" CD on my WinXP Dell 8400 yesterday so decided to install Ubuntu on my old Gateway G6 PII 400, 384 megs of RAM.  

I used the "install" CD in my CD-DVD ROM drive on the Gateway.  I tried tried to install on a 10gig Maxtor freshly wiped and formatted drive - formatted using Win98 Gateway boot floppy.  Install went on for 20 minutes or so, got a screen showing the "Ubuntu" in brown logo.  Then, got a message:

Disk error 01, AX=428D, drive 9F
Boot failed: press a key to retry

Can't get anything to work.  Shutdown and tried to use "live" Ubuntu 5.10 CD that worked on my WinXP Dell.  No go.

Any ideas?  Please remember I will need basic help as I know next to nothing about Linux or Ubuntu.  Thanks in advance.

DE Retiree

---

### Post by Teroedni on 2006-03-10
Do you known how to get into bios

Make sure cd is set to first boot

---

### Post by tyspot on 2006-03-10
Ubby newbie here to but I will give a few stabs in the somewhat dimly lit room i am in. 
What speed is your CD-DVD rom drive on that Gw unit? Look into the boot options and see if there is one that pertains to the speed of the drive. I also suspect that you will need to use a lovga settting in the install but can get better graphics later.

Hope it helps ya in the Spot.

---

### Post by DE Retiree on 2006-03-10
Reset BIOS to CD drive first boot, it had been second after the floppy.  Still no go.  Says "invalid system disk" after several minutes of trying to load.

??????


DE Retiree

---

### Post by Teroedni on 2006-03-10
The cd may be corrupt

Try to burn a new at low speed.

Its happen to me before(corrupt cd )

---

### Post by DE Retiree on 2006-03-10
I'll try to burn another copy.  Thanks for your efforts.

Later,      DE Retiree

---

### Post by DE Retiree on 2006-03-10
Burned another copy.  Seems to be working.  I'm about half way thru the installation.  Had a couple of glitches that seem to have worked out:  got message that "your cd-rom could not be mounted, try again?"  I selected yes and installation proceeded.

My question:  My cd-rom drive seems a bit strange.  I'm considering another one.  Newegg had NEC 3500A on sale this weekend.  I noticed it requires WinXP to operate.  Will it work with Ubuntu??  Sorry for the questions, but I know almost nothing about Linux systems.

Regards,    DE Retiree

---

### Post by DE Retiree on 2006-03-10
Well, I spoke too soon.  At 80% complete on the installation, I'm getting an error message that says "problem reading data from cd-rom.  Failed to copy file.  Retry?"  I clicked yes about a dozen times and it still won't read the file.  Suggestions?

DE Retiree

---

### Post by DE Retiree on 2006-03-12
Thanks to everyone for the help re. my installations issues.  I did have a sometimes defective DVD/CD ROM drive.  I replaced the drive and was able to load from the Breezy Install file just fine.  Thought you would want to know in case someone else ever has a similar problem.  

DE Retiree

---

### Post by BoneKracker on 2006-03-12
Okay - disregard - I see you got it now.  I'll leave the following in case it's useful to anyone else.

--------------------------------------------------------------------------------------------------------------------------------------------
It sounds to me like the problem is CD-related.  I gather from your earlier comments that you are downloading and burning your own copy of the CD (i.e., that you are not using one of the mass-produced ones you can get mailed to you).  If that is true, there are a couple of things you can do to make sure you have a healthy copy of the ISO file and that you have created a healthy CD.

1.  When you download the CD Image, also download the corresponding MD5 checksum file.  Get an MD5 checksum on the ISO file you have downloaded and compare them.  If they agree, you can be relatively confident you have a healthy copy of the ISO file.

2.  When you burn the CD, select a slow burn speed.  The main thing is that you want to avoid exhausting the write buffer during the burn.  Use your experience with the drive and the disks, any test functionality built into the burning software you are using, and the general rule of thumb that slower is better.  I suggest trying 4x or 2x if you aren't sure.  If the burning software you are using provides a "validate" function that checks the integrity of the written files when it's done, use that too.

3.  Assuming you are using the 5.10 "Breezy" install and not the new "graphical" installer with which I'm not familiar.... (there's probably a way to do this using the new CD's too, but it probably won't be exactly as follows).  When you begin your installation, the installation CD presents you with a "boot:" prompt.  At this prompt, you probably just hit "enter" last time.  Instead, you can use the "expert" install to access a function that tests the integrity of the install CD, then if it's okay, abort the "expert" install and do a normal install.  

At the "boot:" prompt, press "Tab" to view all the boot options.  Type out the one that corresponds to the type of installation you want, with the addition of "-expert".  Proceed to follow the prompts as best you can until you are presented with the long menu with all the steps.  Down at the bottom are a couple of items that don't necessarily have to be done in order with the rest -- one of them is something to the effect of "Validate CD Integrity".  Choose that.  When it's done it will report the results and bring you back to the menu.  Assuming it was successful, you can then choose "Abort the Installation" and proceed as you normally would have with the default install.

These suggestions may not solve your problem, but they should rule out the possibility that you are working with a bad CD.

Also, try not to get frustrated.  Part of the magic of Linux is that it will make you learn.  Every user goes through this type of thing at first.  As you master each challenge, you will gain an understanding and degree of control over your computer you never had with Windows enabling you to do things you could never do before.  Don't be afraid to keep posting your results here as you go -- there are lots of people who will happily help you.

---

### Post by adamkane on 2006-03-13
Fantastic followup. "Good Ubuntu!"

---

