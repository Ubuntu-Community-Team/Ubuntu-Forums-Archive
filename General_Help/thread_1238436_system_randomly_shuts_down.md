---
title: "system randomly shuts down"
date: 2009-08-12
forum: General Help
---

### Post by Ygon on 2009-08-12
I am new to Ubuntu, I have had it working perfectly fine for the past week but all of the sudden it will freeze and shut down.  It seems to happen when I am using firefox on flash heavy pages.  I reinstalled Ubuntu thinking maybe something I had installed was causing the problem, but I am still having the same issue.  Don't know what could be causing this, any help would be greatly appreciated.

Thanks

Ygon

---

### Post by P4man on 2009-08-12
most likely a hardware issue. Either something overheating, or your powersupply.

---

### Post by sports fan Matt on 2009-08-12
mine just had the same occur, in my case it was a faulty power supply

---

### Post by Ygon on 2009-08-12
everything on this computer is brand new.  How can I check the cpu temp on Ubuntu?

---

### Post by P4man on 2009-08-12
you can install hardware monitoring tools, its not too hard, but its probably just as easy to quickly go in to your bios and have a look there. If it is a cpu overheating issue, it should be apparent in the bios as well.

Another thing you can do, is open the case and check if the cpu and gpu fan are actually running. Another poster recently here posted that under jaunty his gpu fan did not turn, causing all sort of badness.

If temps are not the issue, check your voltages in the bios. If they are good, it doesn't prove your psu is okay, but if they are way off, it might give a good clue as to what the problem is.

---

### Post by Ygon on 2009-08-12
ok I took some readings my cpu is running at 44.5 c 
cpu v = 1.26v
3.3v = 3.296v
5v= 5.04v
12v = 12.096v

not sure what any of the volt readings mean? I am running an e5200 dualcore intel chip not sure if thats normal temp for that chip either? 

Thanks

Ygon

---

### Post by P4man on 2009-08-12
that all looks normal. Your cpu isnt overheating, those voltages look fine. Im still not ruling out a bad powersupply though.

Also, did you check if the fans, especially the videocard fan is running when in ubuntu?

---

### Post by Ygon on 2009-08-12
How can I test the power supply? its a brand new lsp 450w power supply.  I checked all my fans and they are all running including the video card fan.  My video on my screen also starts acting up right before it freezes and restarts.  Like it takes a long time to load on occasion or it loads crooked and than corrects itself.

---

### Post by P4man on 2009-08-12
what videocard do you have, and what drivers (if any) did you install?

---

### Post by Ygon on 2009-08-12
I have a GeForce GTS 250, I installed the Nvidia accelerated graphics driver(version180) which is recommended through the Hardware drivers interface.  I think its getting worst I just turned my computer on and it shut down right away.  Thanks for all you help.

Ygon

---

### Post by P4man on 2009-08-13
You mean it shut down before it even booted ubuntu ? If so, definitely time to take it back to the shop and get the powersupply (most likely) replaced.

---

### Post by Ygon on 2009-08-13
no it loaded ubuntu and than shut down.  Today its not as bad as it was yesterday,  but when when i try to view a page with flash video my screen will get messed freeze and reboot.

---

### Post by Stavro on 2009-08-13
Hi all, I just noticed this thread and felt compelled to post because I also have the same problem with Jaunty 9.04. The computer in question is about five years old now, but it dual boots XP and only on Ubuntu does it spontaneously freeze then power-down. Especially during flash movies on YouTube. It&#8217;s important to note that I did not have this problem on 7.04 prior to clean installing 9.04. I&#8217;ve seen in other parts of this forum that there could be a bug with Jaunty and power supplies, is this really a possibility? It&#8217;s very frustrating, especially since I have everything including my flash-sound and WIFI that was broken in 7.04 but working perfectly now.

---

### Post by P4man on 2009-08-13
Hmmm. 
An OS doesn't interact directly with a powersupply, but it can shut a machine down through ACPI. If that is what is happening, I'd think there must be some trace of it in the log files. Can you look in system > administration > logfiles and find what happens right before it shuts down?
You could also try disabling acpi in the bios and/or add the acpi=off parameter to the kernel, and see what happens.

The other way a shutdown can occur  is when the motherboard triggers it (eg because something overheats) or the powersupply itself when its faulty, overheating or not powerful enough.

Im not saying this is definitely a hardware issue, but if its an ubuntu problem, I think you should be able to find a trace of it that may help us find a solution. When i google on it, i find tons of people unable to shut down their machines properly, but none really where it shuts down spontaneously.

---

### Post by Stavro on 2009-08-13
Thanks for the reply, I would like to try your suggestion and add acpi=off to the kernel, though I don't know how to do it? Can someone help me please?

---

### Post by Ygon on 2009-08-13
Just wanted to to update on my issue, I took my video card back exchanged it and so far so good. Thanks to all for your help and suggestions.

Ygon

---

### Post by pizmooz on 2009-08-13
just wanted to add:
its always a good idea to take a look at /var/log/kern.log to see if the kernel spit out any info regarding which subsystem the failure occurred in.

---

### Post by Ygon on 2009-08-13
ok I retract my previous post.  It ran fine for a while and now it has restarted by itself again. I am going to try and change the power supply to see if that fixes the problem.  How do I check the logs?

Thanks

Ygon

---

### Post by P4man on 2009-08-14
> **Stavro said:**
> Thanks for the reply, I would like to try your suggestion and add acpi=off to the kernel, though I don't know how to do it? Can someone help me please?

When grub loads, press escape. Then select the top ubuntu kernel, press "e" to edit. Select the kernel line, press again "e" to edit. IT should look a bit like this:

kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=0e5317cf-1aa2-4b20-9ffa-f17c41f48f37 ro quiet splash

at the end, add the acpi switch, so it looks like

kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=0e5317cf-1aa2-4b20-9ffa-f17c41f48f37 ro quiet splash acpi=off

Press enter to confirm, "b" to boot.
Those changes will only affect 1 boot, next time you reboot, they will be gone (acpi will be on again). But should it help, we can make it permanent.

Other switches you might try:
noapic
nolapic

and both of them.

Another thing you can try, is picking an older kernel from the grub menu, if there is one. Pick the oldest one in the list (lowest number), and see if it makes a difference.

good luck

---

### Post by P4man on 2009-08-14
> **Ygon said:**
> ok I retract my previous post.  It ran fine for a while and now it has restarted by itself again. I am going to try and change the power supply to see if that fixes the problem.  How do I check the logs?

Thanks

Ygon


system > administration > log file viewer

---

### Post by Ygon on 2009-08-14
I have replaced the power supply and that hasn't cured the problem.  I did get the following error this time. "Failed to get connection to session: failed to connect to socket /tmp/dbus-UjjtKfjTos connection refused.  Failed to contact configuration server.  enable tcp/ip networking for Orbit ot you have stale NFS locks due to system crash. "  This is all chinese to me, what does this mean and how can I fix this.  Thank you in advance.

Ygon

---

### Post by P4man on 2009-08-14
bummer :s Had hoped the PSU would have cured it :s

What you have now is probably a result of unexpected shutdowns. Is it loading up at all? If not, try the following commands but be VERY careful to type it in right:

```

sudo -i
cd /tmp
rm -rf *
rm -rf .??*
```

**make sure** you are in /tmp before executing those rm (=delete) commands ! 

As to what now to cure the shutdowns.. a different kernel I guess. Did you try loading an older kernel from the grub menu ?

---

### Post by Ygon on 2009-08-15
ok I have exchanged the motherboard just to make sure it was not a hardware issue and that did not fix anything. I have since than installed ubuntu 8.04 that seams to be working better it had not crashed for 2 days.  I installed the adobe 10 flash player from the adobe site and the minute i opened a flash video on the web it crashed,  I reverted back to the flash plugin-non free through symantic package loader and so far so good however my audio is horrible?  How can I fix this?  I will not change anyhing on my system for a few days and see if doesn't happen so I can try to isolate what's causing the problem.  

I also read in another thread people are having the same issue, and it may be due to Compiz, not sure what that is and how to turn it off?

thanks

Ygon

---

### Post by antonius on 2009-08-15
Simple question....does this happen in Windows?  That will give you a yes or no answer of whether it's an Ubuntu problem, or a hardware problem.  If it doesn't happen in Windows, try another distro, to then find out if it's an Ubuntu problem, or a Linux problem in general.  Nobody around here seems to want to think that it could POSSIBLY be a problem with Ubuntu, when in fact, it could easily be that as much as anything else.  Good luck, buddy.  Hope this common sense approach to trouble shooting doesn't get me banned. 


antonius

---

### Post by antonius on 2009-08-15
ALSO...it seems that your cpu may be overheating, like many others said.  A good way to tell would be to use the cpu scaler, and set it on the lowest level, then stress test (two or three flash videos should do the trick).  This was how i realized eventually what was wrong w/ my old system.  Also, take the case off, and watch your fan.  Some implementations of the linux kernel, and some hardware, just don't communicate well.  If THIS is the case, well, see my above comment....

Good luck again..

antonius

---

### Post by Ygon on 2009-08-16
Antonius thanks for the suggestions I will give them a try.  One quick question though what's a cpu scaler? How do I get it?  I will set the my cpu fan on the highest speed through the bios and see if that helps.  I am starting to think it has something to do with firefox, I have installed firefox 2 and that seems to work much better all though it does still crash after playing flash videos or going to web pages heavy of flash it does seem to go much longer before it crashes.  

On a different note I am trying to install nvidia-glx-180 through synaptic manager and its not there?  I have set it to download from the main ubuntu server and  checked of all the repositories but  the package is  still not there.  

Unfortunately I don't have a windows  disc to install , however if I can't get this to work I will have to purchase it and install it.

Thanks again for all your help.  

Ygon

---

### Post by Malcy on 2009-08-16
I'm having a similar issue, sudden power off and reboots. It's not a faulty hardware issue and is definitely related to Firefox and Flash. I am using Chromium and Opera without problem and Windows is fine too. The trouble is that the power off is so abrupt, nothing is recorded in the logfiles.

---

### Post by Ygon on 2009-08-16
thanks for the heads up I am going to give those two a try and see if that gets rid of my issues.

---

### Post by Ygon on 2009-08-16
ok no more problems shutting down, now how in the world do I get flash to work on Opera.  I have tried flash plugin nonfree and adobe flash plugin non of them seem to work.

---

### Post by Malcy on 2009-08-16
Download the latest flashplayer 10 from Adobe Labs. Extract libflashplayer.so and put it into the /usr/lib/opera/plugins folder (you will need to be superuser for this).

Then in Opera go to Tools, Preferences, Advanced, Content, Plug In Options..., Change Path and make sure that the path /usr/lib/opera/plugins exists and is selected. If the path /usr/lib/mozilla/plugins exists, make sure that it is deselected.

Flash should now work.

---

### Post by myamotoman on 2010-12-29
I have the same issue. Ubuntu 10.04 on an HP  Compaq 8710p Ram 2.0Gb
Processor 0 and 1 Intel(r) Core(TM)2 Duo CPU T8100@2.10Ghz
Video is NVidia Quadro NVS 320

Twice now in 3 days i have had reboots. This occurred while surfing and on You tube , with 3 screens open on desktop using the Gimp 

In logs -message i found this  
Dec 29 09:03:46 -laptop -- MARK --
Dec 29 09:23:46 -laptop -- MARK --
Dec 29 09:43:46 -laptop -- MARK --
Dec 29 09:49:01 -laptop pulseaudio[2995]: pid.c: Stale PID file, overwriting.
Dec 29 09:49:01 -laptop pulseaudio[2995]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-f8o1COlDUO: Connection refused
Dec 29 09:49:05 -laptop bonobo-activation-server (-3026): could not associate with desktop session: Failed to connect to socket /tmp/dbus-f8o1COlDUO: Connection refused
Dec 29 09:52:31 -laptop syslogd 1.5.0#5ubuntu4: restart.


Not sure what it all means. 

I did have a new Mother board installed and a Screen 3 mos back under warranty. System is dual boot With Win 7 Pro. never reboots on Win 7

---

