---
title: "Ubuntu freezing to death on a thinkpad"
date: 2006-04-22
forum: General Help
---

### Post by volland on 2006-04-22
Hey All,

I've just now moved to Ubuntu from Windows, but I'm forced to write this message from Windows. The thing is, yesterday I've finally had the chance to do some serious configuring work on my linux - or at least I tried. (The machine is an IBM Thinkpad T42, 1GB RAM) 
At some point, I closed the lid ( = moving to Standby-to-memory mode) and went away (the laptop was plugged in the power). When I came back, it wouldn't come back up. In fact, it didn't respond at all - just a black screen. I've tried everything, including short/long pressing on the power button, nothing. Finally I've removed and then put the battery back in, and then it booted. 
After this, it happened two more times - computer totally freezes, not reacting to anything - and the last time wasn't even after a standby! It was just in the middle of my work! As someone who's been told by linux zealots/friends of the wonders of Linux's stability, and as someone whose XP didn't crash for ages, I find this rather disappointing.

Any ideas?

---

### Post by bscbrit on 2006-04-22
A few thing to check:

Have you selected the option to go to hibernate when you close the lid?

Do you close down the computer properly before switching it off?

What version of Ubuntu are you using? (Don't forget, Dapper is still in testing and hasn't been released yet ;) )

What were you doing when it froze in the middle of your work?  If you can give us a clue, we might be able to diagnose the problem.

---

### Post by volland on 2006-04-22
Oh, of course. I forgot to mention I'm using 5.10. 

Um, regarding the hibernate, I honestly can't remember. But judging by how quickly it would resume from standing by in the past, I don't think so. Plus, if the default would be to not hibernate, I don't see any reason I would change it.

Yes, I'm closing down my computer properly.

Um, I don't recall doing anything special. Some browsing using Firefox (btw, why isn't Ubuntu pre-bundled with 1.5?), going through files, trying to copy things within the home dir (but nothing that could cause such a thing, in my opinion).
Anyway, since the last freeze didn't follow any action on my using - I was just reading a pdf - I doubt it was directly effected by my actions.

---

### Post by bscbrit on 2006-04-22
When it freezes, what do you have to do to recover it:

1. Wait until it becomes responsive again? (perhaps wait 15 minutes and see what happens)

2.  A power recycyle using the on/off key?

3.  A power recycle because nothing works, not even the power key?

Yes, I have read your first post but I was thinking more of the freeze when you were looking at a pdf.

---

### Post by volland on 2006-04-22
Steps 1&2 didn't work during the first two freezes, so I didn't even try the third time (I know, it's bad, but I tend to lose my temper quickly). Yes, all three times I've removed my battery, unplugged it from the AC, and waited a few minutes.

---

### Post by fyrestrtr on 2006-04-22
A few things to check (I am also on a Thinkpad but a different model than yours -- T43 2668-71G) and have not faced this problem.  Just tested it by closing the lid, waiting, and opening it up again.

1. Does your laptop come with an ATI card? The binary drivers from ATI provide better suspend/resume support than the ones that are available from the repositories.  Install the binary drivers by reading the howto at the wiki.

2. Have you enabled the ibm_acpi module? It is built by default into the kernel, and it will give you better support for power management (in addition to other benefits like making your fn keys work, and providing temperature sensors).  A few steps to do if you want to load this module:

* Make sure it is compiled in.  I did not test on Breezy, but on Dapper it was available in the default kernel.  To see if its available, type this:

```

$ lsmod | grep ibm
ibm_acpi               26080  0

```

You should get the same output as mine.  If this module appears; you might need to load it.  You can add ibm_acpi at the end of your /etc/modules file and see if that helps.

It is really strange that your Thinkpad is hard freezing because it cannot suspend back.  How much free space do you have on your hard disk?

If nothing else helps, try looking up your model at the [ThinkWiki](www.thinkwiki.org/wiki/ThinkWiki) (might want to bookmark this, a great resource for running Linux on Thinkpads).

---

### Post by volland on 2006-04-29
Well, it's happenned again today, several times -- sometimes even minutes after the computer came up, and either way, **way** too often. It's getting ridiculous. This has nothing to do with hibernation / standby - it's occured smack in the middle of my work, an no apperant action of mine triggered it. The only common status to all the freezes I can point to is that I was using Firefox, bu that's not much, since that's mostly what I do with my laptop anyway. The one thing I have been able to do is to reboot using a 10-second press on the Power button, instead of disconnecting the battery.

After googling on this a bit I thought that perhaps I've caused some sort of physical shock to the laptop during my travels with it yesterday, but since I've booted Win XP it's been ok for several hours now. So I'm quite confident this isn't some hardware malfunction.

Please, I much rather use Ubuntu, can someone advise at least on an appoach I should try to solve this?

---

### Post by kenweill on 2006-04-29
[QUOTE=volland]Hey All,

I've just now moved to Ubuntu from Windows, but I'm forced to write this message from Windows. The thing is, yesterday I've finally had the chance to do some serious configuring work on my linux - or at least I tried. (The machine is an IBM Thinkpad T42, 1GB RAM) 
At some point, I closed the lid ( = moving to Standby-to-memory mode) and went away (the laptop was plugged in the power). When I came back, it wouldn't come back up. In fact, it didn't respond at all - just a black screen. I've tried everything, including short/long pressing on the power button, nothing. Finally I've removed and then put the battery back in, and then it booted. 
After this, it happened two more times - computer totally freezes, not reacting to anything - and the last time wasn't even after a standby! It was just in the middle of my work! As someone who's been told by linux zealots/friends of the wonders of Linux's stability, and as someone whose XP didn't crash for ages, I find this rather disappointing.

Any ideas?[/QUOTE]

The problem is specific to IBM machines. Not just on ThinkPad, but also in ThinkCentre.

If you are using Ubuntu Breezy, add "noapic" and "apic=off" in your kernel paramenter.

If you are using Ubuntu Dapper(Beta or whatever), add "noacpi" and "acpi=off" in your kernel parameter, since "noapic" and "apic=off" doesn't work on Dapper.

I don't know if there are other solutions but it worked with my IBM machines.

---

### Post by volland on 2006-04-29
I'm on breezy. Could you please tell me how to add anything to the kernel parameters? I'm very new to linux. Thanks.

---

### Post by kenweill on 2006-04-29
[QUOTE=volland]I'm on breezy. Could you please tell me how to add anything to the kernel parameters? I'm very new to linux. Thanks.[/QUOTE]

First, open up a terminal. Click on Applications->Accesories->Terminal
Then type: "sudo gedit /boot/grub/menu.lst"
Then scroll down until you find a line that looks like:

kernel		/boot/vmlinuz-2.6.15-21-386 root=/dev/hda1 ro quiet splash

On breezy, it could be different. The line above is taken from my menu.lst file. The numbers should be different depending on your kervel version.

Then add the line "noapic" and "apic=off". It should look something like this.

kernel		/boot/vmlinuz-2.6.15-21-386 root=/dev/hda1 ro quiet splash noapic apic=off

Then restart your computer.

---

### Post by volland on 2006-04-29
Well, thanks, but this didn't work. About five minutes after the reboot it froze up again. Any other ideas?

---

### Post by Loevborg on 2006-04-30
[QUOTE=kenweill]First, open up a terminal. Click on Applications->Accesories->Terminal
Then type: "sudo gedit /boot/grub/menu.lst"
Then scroll down until you find a line that looks like:

kernel		/boot/vmlinuz-2.6.15-21-386 root=/dev/hda1 ro quiet splash

On breezy, it could be different. The line above is taken from my menu.lst file. The numbers should be different depending on your kervel version.

Then add the line "noapic" and "apic=off". It should look something like this.

kernel		/boot/vmlinuz-2.6.15-21-386 root=/dev/hda1 ro quiet splash noapic apic=off

Then restart your computer.[/QUOTE]

Remember to run "sudo update-grub" after changing your menu.lst in order for the changes to that file to take effect,

---

### Post by volland on 2006-05-03
[QUOTE=Loevborg]Remember to run "sudo update-grub" after changing your menu.lst in order for the changes to that file to take effect,[/QUOTE]

Well, this doesn't work neither. Notice a very odd thing: I've noticed this only happens at home. When I take my laptop to my brother's house, or my university, the linux works just fine, for hours. I find this very bizarre. The only explanation I see here is that perhaps the wireless router I have at home (a Level One router) somehow manages to crash Ubuntu. 

Any thoughts?

---

### Post by bscbrit on 2006-05-05
It could conceivably be excessive noise on the mains supply but this fault would be most unusual for a laptop.  Does it occur when running on the battery?  If not, then it might well be something to do with the mains supply but if it does occur when using the battery then it cannot be the mains.  :D

---

### Post by bscbrit on 2006-05-05
Another thought - do you have network-manager installed?  This program has been seen to cause problems on some computers although many other users have no problems whatsoever.

HTH - but I can't stay online for long as this is not my computer....;)

---

### Post by likerice on 2006-05-09
i had the same problem with my t42 (2378-fvu) until yesterday. now it's fixed. no more random and frequent hard freezes.

i searched everywhere online for similar problem reports, but found none. i stumbled upon this post and tried the suggested remedies, but to no avail.  

in desperation, i logged into windows and used the "access ibm /  lenovo productivity" thing (avalailable at [http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=SOFT-UPDATE](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=SOFT-UPDATE) for windows only) to update the bios and whatnot. now the problem is fixed. causation? who can say? but the hard freezes which siezed my laptop seemingly at random have since ceased. 

what could have caused the problem, and what's to explain the fix? 

i suspect the problem was wireless related, but this is only a hunch. 

it 's also worth noting that my T42 had worked beautifully with ubuntu for months, the problem having surfaced only within the last week, in which both of the following occurred:
1. system board replaced by ibm after a tea spilled atop the table upon which my laptop had been resting and seeped upwards through the docking port
2. i upgraded my linux kernel to 2.6.12-10.32 from 2.6.12-10.23 and agreed to a barrage of other recommended updates via synaptic.

the mystery persists.

---

### Post by Mitush on 2006-05-10
I am contemplating getting a new T42 and stumbled on this thread. Did you guys resolve the problem with the bios update?

---

### Post by volland on 2006-05-10
[QUOTE=Mitush]I am contemplating getting a new T42 and stumbled on this thread. Did you guys resolve the problem with the bios update?[/QUOTE]

I havn't tried it yet. Will do this in a couple of days and report. Sounds like it couls fix it, though.

Anyway, as the lack of Google results show, it's probably a rare problem, which might be connected to the type of wireless internet you're accessing. I don't think this should deter you from getting a T42.

---

### Post by likerice on 2006-05-11
i've encountered another, potentially related issue since i replaced my system board and updated the kernel etc. (see above): i've lost the ability to recover from suspend (not hibernation, which i've not thus far enabled). 

this issue is potentially related, i say, because the system hard-crashed (froze) once when attempting to recover from suspend and the second time it cycled a message about the x terminal, which i neglected to write down. 

curioser and curioser, i say.

and to the earlier question about the t42, i have no hard and fast recommendation either way. suffice it to say, however, that given my present complications, i cannot give in good conscience an unqualified endorsement of the laptop.

---

### Post by volland on 2006-06-02
[QUOTE=likerice]i had the same problem with my t42 (2378-fvu) until yesterday. now it's fixed. no more random and frequent hard freezes.

i searched everywhere online for similar problem reports, but found none. i stumbled upon this post and tried the suggested remedies, but to no avail.  

in desperation, i logged into windows and used the "access ibm /  lenovo productivity" thing (avalailable at [http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=SOFT-UPDATE](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=SOFT-UPDATE) for windows only) to update the bios and whatnot. now the problem is fixed. causation? who can say? but the hard freezes which siezed my laptop seemingly at random have since ceased. 

what could have caused the problem, and what's to explain the fix? 

i suspect the problem was wireless related, but this is only a hunch. 

it 's also worth noting that my T42 had worked beautifully with ubuntu for months, the problem having surfaced only within the last week, in which both of the following occurred:
1. system board replaced by ibm after a tea spilled atop the table upon which my laptop had been resting and seeped upwards through the docking port
2. i upgraded my linux kernel to 2.6.12-10.32 from 2.6.12-10.23 and agreed to a barrage of other recommended updates via synaptic.

the mystery persists.[/QUOTE]

Well, this too failed. I've updated everything as you described. A week later, I've launched Ubuntu at home, it froze within seconds after openning the first site on Firefox. So I'm confident now it has something to do with my wireless. How can I solve this? Maybe I could try Dapper Drake - could this magically help?

---

### Post by cjbriere on 2006-06-03
I have a t42p and I was having alot of the problems mentioned above. The fix for me was to update my bios on my laptop. Definately worth a shot.

---

### Post by volland on 2006-06-03
[QUOTE=cjbriere]I have a t42p and I was having alot of the problems mentioned above. The fix for me was to update my bios on my laptop. Definately worth a shot.[/QUOTE]

I've done this already, using IBM default automatic installer. Didn't help.

---

### Post by likerice on 2006-06-03
yes, i can confirm that a bios update does not resolve the problem. several weeks ago, i re-installed ubuntu and declined to apply any of the package updates recommended by synaptic. my laptop had initially worked perfectly when i had first begun to use ubuntu; the problem only emerging after a recent series of updates. thus, i thought that there might have been something wrong with one of those packages.

my t42 worked perfectly under heavy usage for the next month until, oddly enough, i visited this forum to check the latest posts 2 days ago. the computer hard-froze again ](*,) 

the problem, as mentioned earlier, seems to be related to certain wireless networks under certain conditions. my t42 works perfectly at home using my own wireless network as well as my neighbor's network ;-) my most recent hard-freeze described above occurred after i connected to my friend's wireless network in beijing. i'm currently still using my friend's network via ethernet cable. i've turned off my wireless card (Fn + F5) and everything seems to be working well. this obviously is not a long-term solution to the problem.

has anyone updated to dapper yet to see if the hard-freeze persists? and are others using "network-manager", as am i, to establish wireless connectivity rather than the default thing (whatever it was called)? 

damned annoying problem, this.

---

### Post by volland on 2006-06-04
Havn't upgraded to Dapper yet, sounds like an interesting idea. But requires mroe time than I have at the moment. Has anyone alerted the developers of this issue? So that this'll be tackled in Dapper?

I think I'm using the default thing, can't remember.

---

### Post by BeachBum on 2006-06-08
I had somewhat similar problems with my T42.  Frequently (NOT every time) I opened OpenOffice I experienced some very hard crashes and complete lockups.  Sometimes it occured immediately, sometimes it took a few seconds of interaction with the program to lock up, and sometimes it didn't lock up at all!  In the situations that it did lock up, I had to hard reboot and upon reboot, root was unmountable!  I had to boot using my trusty Debain cd, mount the drive and run e2fsck (scandisk/chkdisk equivelent) on it before I could boot.  

The linux system and kernel logs showed no unusual behavior, however upon locking up the hard drive made a very strange and eerily rhythmic clicking/ head seeking noise.  Did loads of research and it turned out that my hard drive was failing.  smartctl (linux program for monitoring s.m.a.r.t. status) indicated impending failure, so I found a Windoze-compatable utilitiy (a bootable Hitachi harddrive diagnostic disk), and confirmed the errors.  All the while, Windoze worked...well...fine.  I called up Lenovo and told them about "programs locking up" and that the Hitachi program reported a high number of bad sectors and actually locked up with a red screen that displayed FAULTY DEVICE in nice big letters.  I didn't want to mention I had Linux on my Thinkpad, as Lenovo most likely does not support it ;) .  2 days later, shiny new hard drive, and everything works nicely.  

What I think happened was whatever sectors OpenOffice was written to "went bad" (possibly from me jarring the laptop while moving from desk to couch), and as a result caused problems anytime I used OO.  Get smartctl (from repos) and see if maybe your harddrive is causing problems.  

This entry from the Gentoo Wiki helped me get the program running:
[http://gentoo-wiki.com/HOWTO_Monitor_your_hard_disk(s)_with_smartmontools](http://gentoo-wiki.com/HOWTO_Monitor_your_hard_disk(s)_with_smartmontools)
Just skip the installation procedure and start with Using smartctl.

This is the Hitachi Drive Fitness bootable ISO. 
[http://www.hitachigst.com/hdd/support/download.htm](http://www.hitachigst.com/hdd/support/download.htm)
I'd recommend using this if smartctl reports errors, as you don't want to waste a good cd!

Good Luck!

---

### Post by Artemis3 on 2006-06-15
Hello: I want to share with you the horrible experience about this issue.

I have had access to way too many IBM ThinkCentres and this issue is not funny... In an event there were like 30 of them with hoary installed. I'm working in a place where they are considering massive migration to free software and i'm seeing these machines all over the place.

So my experience is this: About 9 of 10 IBM ThinkCentres (Models MT-M and friends) show this behaviour. I can confirm this problem happens with Ubuntu: Hoary, Breezy and Dapper (releases). With Dapper, the livecd which is now the "desktop" install, the issue triggers so fast that can't even reach the second screen of the install program.

The problem is as follows: Machine boots and works fine. After a while (this can take anything from a couple of minutes to a couple of hours) the machine starts getting slower and slower, and then even typing something in a console gets like 15 minutes or so and you end rebooting or shutting down.

The problem is related with ACPI or whatever they like to call the power thingie these days. After who knows how much frustration, i found the cause to be a problem with IBMs and the default kernel compile coming from Debian.

The corresponding debian bug is: #284477 Titled: **kernel-image-2.6.8-1-686: IBM ThinkCentre sometimes goes to extremely sluggish state**.

This does not occur with all IBMs, for some, upgrading the bios seem to cure the problem, others would simply recompile the kernel removing acpi.

To install ubuntu, and recompile before the bug is triggered is very difficult.
Other distros and OSes like freebsd work just fine.

In the meantime Ubuntu and IBM machines are a big NO. I suggest Canonical pays special attention to this and get one of these dreaded IBM ThinkCentres to test. The one i'm typing this is the MT-M 8149 where the problem occurs even after a bios upgrade.

If you need more information about what this problem does, please read the comments of [Debian Bug #284477]("http://bugs.donarmstrong.com/cgi-bin/bugreport.cgi?bug=284477") i can confirm this has happened to me in many IBM machines i have tried ubuntu with.

---

### Post by Artemis3 on 2006-06-17
I tried noacpi acpi=off and it worked. 

BUT, the machine i tried the livecd with, had 256mb of ram, and the install program seems to need more memory as it never finishes changing a page.

So, i killed the gnome, hand edited a .xinitrc to load just a single xterm; ran startx and then manually ran 'sudo ubiquity' to make the install possible.

In short, don't use "desktop" install unless your machine has lots of memory...

---

