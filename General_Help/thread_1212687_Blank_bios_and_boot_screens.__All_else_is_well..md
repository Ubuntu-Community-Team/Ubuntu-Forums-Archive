---
title: "Blank bios and boot screens.  All else is well."
date: 2009-07-14
forum: General Help
---

### Post by aum11 on 2009-07-14
When I shutdown 9.04 the screen does blank, even though the shutdown is occurring perfectly.  When I boot the laptop again, there is no dell startup or bios screen, or boot screen.  It automatically boots into the default os....9.10.  The login screen appears and all is working perfectly.

Of course the problem with this blank screen behaviour is that I cannot boot into any of the other os's on my system, including live cds.

What could have happened and how can I fix it please?

This is on a newish dell 1710 with 4gb of memory and running 64 bit Jaunty.

---

### Post by itsjareds on 2009-07-14
Have you tried pressing ESC the whole time before you reach the boot splash? I'm not sure what happened to your BIOS screen, but your GRUB menu may have been hidden. Pressing ESC will show other options.

---

### Post by aum11 on 2009-07-14
Thanks itsjareds.

Tried that but the dell and boot screens are still blank, and the system eventually gets to the login screen.

I am confident that verything is working fine behind the blank screen, and we simply need to turn on the visuals.

---

### Post by aum11 on 2009-07-14
Any suggestions please

---

### Post by aum11 on 2009-07-15
i am really confused.

What could make the screen blank for shutdown , Dell initial boot screen, boot options screen and Ubuntu boot process(not even the progress bar, and then reappear for login screen and all usage of Ubuntu?

Suggestions please?

---

### Post by itsjareds on 2009-07-15
Do you have your comp hooked up to a computer?

From a Google search, one guy plugged his monitor into the wrong port for his graphics card after he moved his computer. Got the same problem as you did.

[XP Pro boots, but cannot see or access BIOS bootup screens]("http://www.techsupportforum.com/hardware-support/motherboards-bios-cpu/119745-xp-pro-boots-but-cannot-see-access-bios-bootup-screens.html")

(That page timed out for me, [here's Google's cached version]("http://74.125.47.132/search?q=cache:3aNtFyCUBz0J:www.techsupportforum.com/hardware-support/motherboards-bios-cpu/119745-xp-pro-boots-but-cannot-see-access-bios-bootup-screens.html+cannot+see+bios+screen&cd=3&hl=en&ct=clnk&gl=us&client=firefox-a") if it does for you too.)

Did this happen suddenly on reboot or had you done something beforehand?

---

### Post by aum11 on 2009-07-15
No it is stand alone.
Thanks.

---

### Post by philcamlin on 2009-07-15
aha this is kinda of a last ditch effort but why dont you just start madly hitting f12 or f2 as soon as you power up to try top get into the bios :D:popcorn:

---

### Post by itsjareds on 2009-07-15
It sounds like this is a fairly common problem not with Ubuntu but just with computers in general.

[http://www.tomshardware.com/forum/235632-45-cannot-bios-post-windows-boots-fine]("http://www.tomshardware.com/forum/235632-45-cannot-bios-post-windows-boots-fine")
[http://www.fixya.com/support/t2328270-see_bios_or_dual_boot_option_brandnew]("http://www.fixya.com/support/t2328270-see_bios_or_dual_boot_option_brandnew")
[http://forums.nvidia.com/index.php?showtopic=89441]("http://forums.nvidia.com/index.php?showtopic=89441")

I'm searching Google for an answer, but so far I haven't seen any solutions. Mostly just threads that never got answered.

---

### Post by aum11 on 2009-07-15
Believe me I have and still nothing show up...even though it seems to be processing ok behind the blank screen

---

### Post by itsjareds on 2009-07-15
Woops, i said the wrong thing earlier. Is your comp hooked up to a TV (not a computer)?

---

### Post by aum11 on 2009-07-15
It seems as if the screen is turned off when Ubuntu goes into the shutsdown process and is only turned on again at the time of creating the login screen......????????????

---

### Post by itsjareds on 2009-07-15
Have you changed anything in your BIOS recently?

edit: Here's another thread:

[http://en.community.dell.com/forums/p/19080993/19362884.aspx]("http://en.community.dell.com/forums/p/19080993/19362884.aspx")

Have you ever been able to see the BIOS screen? Have you changed your monitor or gotten a new graphics card recently?

edit2: This may also be of interest.. 

[http://ubuntuforums.org/showthread.php?t=722510]("http://ubuntuforums.org/showthread.php?t=722510")

---

### Post by aum11 on 2009-07-15
Thank You!!!!!!!!!!!!!!

As soon as I removed the vga cable connecting to the TV, and rebooted everything returned to normal.

You are a champion....I have been searching for answers for days.

I wonder why it all of a sudden behaved like that, because I usaully have the vga ccable connected.

I will mark this as solved,

Thanks for Your perseverance itsjareds.

---

### Post by itsjareds on 2009-07-16
Great :D

Too bad I typoed on the earlier post, or we could have figured that out sooner :???:

I wonder if there are any settings you can change that will allow you to keep that plugged in. Either way, I'm glad you have things working.

---

