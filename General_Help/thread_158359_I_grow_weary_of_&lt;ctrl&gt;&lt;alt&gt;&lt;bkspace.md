---
title: "I grow weary of &lt;ctrl&gt;&lt;alt&gt;&lt;bkspace&gt;"
date: 2006-04-11
forum: General Help
---

### Post by dmizer on 2006-04-11
so many times a day i have lost track.  i feel like i'm running win 95 again for cryin' out loud.

i know one of my problems is gaim, and i'm working up the courage to roll my own source for it.  but that is not the only problem i have.  nautilus seems to like to crash on me now and again.  and sometimes i have no idea what causes the lock up and nothing works but the dreaded <ctrl><alt><bkspace>.

furthermore ... once i have killed x with <ctrl><alt><bkspace>, i cannot simply log back into ubuntu.  it won't load.  so i try the terminal and look in top to see what's causing the problem, and i kill it ... but it doesn't die.  so my only option is reboot.

my record uptime on this thing is like 8 hours.

i have searched here, and there seems to be no shortage of people with this problem.  most of the fixes seem to be related to acpi ... but i'm running a laptop and i need acpi turned on in order to run my cpu fan.  are there alternatives i'm missing here?  any other way to tackle this problem?

---

### Post by greenstar on 2006-04-11
How much RAM does your box have?

Greenstar

---

### Post by dmizer on 2006-04-11
i am running a 1ghz piii box with 256meg of ram.

---

### Post by greenstar on 2006-04-11
That should be enough. Just thought I'd ask. :)

I've also seen similar behavior as a result of overheating processor and/or RAM. especially the processor. Check to see if the RAM, processor fan & heatsink are dusty. Dust will cause overheating. Clean with a paintbrush or compressed air, I prefer paintbrush because using compressed air makes the dust fly everywhere. I use a good natural hair paintbrush because nylon or polyester bristles might hold  or conduct a static charge.

Also check case fans & look inside power supply, I often find big clumps of dust inside power supply cases.

Sorry if I'm stating the obviuos. Just trying to help.

Greenstar

---

### Post by dmizer on 2006-04-11
no worries about the obvious.  got to start somewhere.

since i purchased the computer used, i've already had it apart and cleaned everything.  fan works fine, and i monitor the cpu temp with gkrelm, and there doesn't seem to be anything temperature related which would cause this.

---

### Post by gord on 2006-04-11
have you tryed running memtest86? (its on the grub boot menu, when you boot up ubuntu), could be faulty ram.

allthough sounds to me like a problem i once had with a faulty computer, never did track down the problem, but i needed a new computer anyway. after a few hours it would just lock up. it was either the processor, motherboard or ram though.

---

### Post by Mustard on 2006-04-11
I'd definitely recommend doing the memtest from the Grub menu at startup.  If you get errors in the memtest, then it's likely that you have a flaky RAM stick.

The symptoms I got with my faulty RAM was an intermittent problem in which the desktop would suddenly start to shut down all applications and the display would reset and leave me back on the login prompt for GDM.

---

### Post by dmizer on 2006-04-11
to be honest, i wouldn't have been surprised if the memory was causing the problem, but memtest86 passed.

---

### Post by OfficeLinebacker on 2006-04-11
This is not a hardware problem, if you can drop to a console and execute commands.  It's a software problem.  I hope this at least points you in the right direction.

---

### Post by dmizer on 2006-04-11
yes, after i kill x with <ctrl><alt><bkspace>, i can drop into safe terminal mode and execute commands with no problem.  the system will freeze if i try to kill an app, but otherwise things work fine.  other than memory, i didn't expect this problem to be hardware related.

however, i'm not too sure how to go about troubleshooting it.  the problem most often seems to be related to the toolbar panel.  i can still switch between open windows using <alt><tab> but whatever application has caused the problem will not function.  sometimes it nautilus, sometimes it's firefox, sometimes it's gaim.

---

### Post by dmizer on 2006-05-02
this problem seems to be related to the sound in some way.  the sound will work fine, but sometimes when an operation calls to make a sound, the sound will fail and then my system becomes useless.

again, i can use currently open apps just fine, i just cannot open any new programs.

still ... the only way i have found to correct this problem is to ctrl + alt + bkspace and reboot (restarting x does not correct the problem).  ps -a does not show anything unusual that i can see, and i monitor top constantly.  nothing seems to be using too much memory or too much cpu.

this is really driving me nuts and i can't figure it out.

---

### Post by djheadley on 2006-05-02
Another obvious solution...Have you  done fsck on the hard drive?  Sometimes a bad spot on the hard drive (or one that's going bad) will give "goofy" problems.

---

### Post by dmizer on 2006-05-09
i have had problems in linux before that were related to hdd problems, but in this case, i didn't consider that as an option.  the system works fine.  just the windows manager locks up.  that's it.

i scanned anyway, and the hdd is perfectly healthy.

thanks for your reply anyway.

i have done a number of things to try to resolve the issue, and it seems to have calmed down quite a bit.
1) i changed all sound settings so everything uses alsa.  that seems to have fixed a majority of the hangs.
2) i updated gaim to 1.5
3) i tweaked firefox to correct some of it's memory leak issues.

at least with the above changes, i can go through several days without a lock, but it's still annoying as hell when it happens.

i understand that metacity can cause problems too.  i'm using brushedC with thin ice and glass icons.  i really like how i have it set up.  i'd hate to have to give up my theme.

as i suspected to begin with, the problem is turning out to be several different issues rather than just one solvable problem.  i learned a long time ago that just because symptoms are the same doesn't mean the cause is the same.

---

### Post by dmizer on 2006-05-24
this issue has started to become an issue again.  now most often i'm getting crashes when clicking to open a directory in nautilus.  the "click" sound it makes when opening a directory starts okay, but then turns into static.  after that, nautilus crashes.  and of course, my entire machine needs to be rebooted before i can open new programs.

once again, i am still able to work just fine in programs that are currently open at the time of the hang, but no new programs can be opened, and panel menus are unusable.

is there some way i can capture an error of some sort when nautilus blows it's top?

---

### Post by OfficeLinebacker on 2006-05-24
Thanks for following up.  Sorry I can't help you but good on you for being persistent.

---

