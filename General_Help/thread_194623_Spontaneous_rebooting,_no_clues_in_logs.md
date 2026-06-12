---
title: "Spontaneous rebooting, no clues in logs"
date: 2006-06-11
forum: General Help
---

### Post by ehammond on 2006-06-11
SUMMARY

Upgraded web server system from Fedora Core 3 to Ubuntu 6.06 (Dapper) using a new disk drive.  System is now spontaneously rebooting on a regular basis.  Not sure if it is a hardware or software issue.  Nothing shows up in any system log before the boot up messages.

Status lights once showed a "possible processor failure" condition. Second processor and hyperthreading were disabled which fixed the problem for a day, then the spontaneous rebooting started again.

I'm trying to work with Dell to solve the problem but would appreciate any pointers and ideas from the experts here on how I might go about diagnosing and isolating the cause of the spontenous reboots, especially if there is any chance it may be related to the new install of Ubuntu.

DETAILS

Dell Precision Workstation 470; 2 x 3.4GHz CPUs; 4GB RAM; 500GB & 230GB SATA hard drives.

$ uname -a
Linux XXXX 2.6.15-23-686 #1 SMP PREEMPT Tue May 23 14:03:07 UTC 2006 i686 GNU/Linux

This machine is used to host:
- DNS (bind9)
- Email (Postfix)
- Web (Apache 2)

Plus, I run my main desktop on it with X (nvidia-glx).

Further hardware and system configuration details available on request.

The system was running fine under Fedora Core 3.  When the primary disk drive went bad, I decided to use the downtime as an opportunity to upgrade to Ubuntu Dapper and installed everything from scratch on a new disk drive (using backups for the data parts of the system).

Everything ran fine for a couple days, then the system started spontaneously rebooting once every day for a few days.  Then the frequency increased to once every hour, then once every 10 minutes, then it seemed to stop with the status lights indicating "possible processor failure".

I disabled the second CPU and turned off hyperthreading on the first CPU.  The system ran fine for a day, then rebooted. It again increased the frequency to once every 10 minutes.

I turned off the web server which is where I am now and the system has been up for almost 2 hours.  This doesn't remove hardware from the equation as not running the web server would simply reduce the amount of load placed on the system.

Things I suspect and would like to isolate:

- CPU. Though I'm not convinced the status lights told the truth that one time, it's an obvious suspect and I'm going to try to get Dell to send me a new one or two.  I may also try running on the second CPU alone after swapping them.

- The new disk drive.  The spontaneous reboots happened after installing a new primary disk drive (on which I installed Ubuntu). I could copy the partitions onto another new disk and see if it continues to reboot.

- The SATA cable connector on the motherboard.  The original Dell SATA cable was short and when the clamshell case is opened pressure was put on the connectors. Not sure if I ever put enough pressure to cause damage or if this would even be able to cause rebooting.  I am using a new (longer) cable.

- The patterns of increasing frequency make me wonder about heat as a cause, but I'm not sure what part(s) it would be affecting.

Questions:

- Anybody else seeing spontaneous reboots with Ubuntu Dapper?

- How can I query the temperature of the CPU?

- Any pointers on making an exactly copy of a disk drive?  I know I can use dd to copy the partitions, but am not sure if anything special needs to be done with the master boot record.

- Any other ideas or suggestions on things I could try?

Thanks

---

### Post by ehammond on 2006-06-11
Update:

- Swapped CPUs (enabling only the first) and it still rebooted spontaneously.
- Unplugged both disk drives, booted from an Ubuntu CD and it still rebooted.

---

### Post by Jott on 2006-06-11
can you check the temperature your cpu is operating at?  This happened to me once, I realised that my sysytem was running waaaaay to hot.

---

### Post by cleentrax on 2006-06-11
Is running X? Is it a full reboot, or just restarting X?

---

### Post by ehammond on 2006-06-11
[QUOTE=cleentrax]Is running X? Is it a full reboot, or just restarting X?[/QUOTE]

It's a full reboot (BIOS F2 setup prompt, grub, ...).  Yes it is running X if it gets that far in the reboot process, but X is not the cause of the reboot because some times it reboots during the reboot phase before X has been started.

The more I investigate and the more I try, the less I think it has to do with Ubuntu.  I'm thinking that it's just a coincidence that I had just installed Ubuntu before the reboots started.

---

### Post by Skye on 2006-06-11
Looking at what you have (2 Intel Pentium 3.4 GHz CPUs) inside a Dell-built machine, I think there's a good chance of it being a heat issue.  Those Intel chips run hot, and all the Dell machines i've ever worked on have had one fan to cool both the system and the CPU, and maybe a fan in the PSU.  I'm not sure if their workstations are any better, but their desktops have always had problems with heat management.

Try running the computer with the case off and a window fan blowing on it.  Also make sure that the fans are actually spinning, that there's not dust in there, etc.

Also, if it's a late-model computer (which it sounds like it is) it should have a temperature monitoring facility somewhere in the BIOS.

Come to think of it, that's one thing you can do to eliminate it being a problem with the OS- boot into the BIOS, and just leave it there, and see if it reboots while there.

Good luck!

---

### Post by ehammond on 2006-06-12
[QUOTE=Jott]can you check the temperature your cpu is operating at?[/QUOTE]

Thanks for the idea.  I'm not sure how to do this.

---

### Post by ehammond on 2006-06-12
[QUOTE=Skye][...] I think there's a good chance of it being a heat issue.  [/QUOTE]

Thanks for your suggestions.  I vacuumed out the dust and ran it for a while with the case open and a fan blowing on it.  It seemed to reboot just as much.

I'm leaving it in the BIOS now per your last suggestion.

The Dell precision workstation 470 has one fan pulling air into the case, one fan for each CPU and one for the memory.  I think they're all running. There's probably supposed to be one in the power supply, but I can't feel any air coming out the back there.  Hmmm...

---

### Post by ehammond on 2006-06-17
The motherboard was replaced and now the system is running fine with no glitches.  This problem was not related to Ubuntu.

Thanks to the ideas and suggestions of things to try from this board.

I'd still like to get pointers on how to check the temperature inside my system. My investigation turned up lm-sensors, but I never figured out how to configure it for my particular system.  It seems like we have a ways to go in automating this, but the Debian / Ubuntu folks have done an amazing job in so many other areas I have high hopes.

---

