---
title: "Ubuntu Is shutting itself off"
date: 2011-08-12
forum: General Help
---

### Post by LinuxSavedMyComputer on 2011-08-12
I have had a problem, yesterday and today my computer shut itself off.
On Wednesday, It displayed a bunch of statements and [OK] messages before shutting off
On Thursday, it shut down using the standard Ubuntu message,
the only thing it seems to have in common is we were streaming flash video and they happend around 9:00-10:00

It is important that this problem be fixed

Help would be greatly appriciated

---

### Post by aeiah on 2011-08-12
what's in your /var/log/messages file for around that time?

---

### Post by LinuxSavedMyComputer on 2011-08-12
> **aeiah said:**
> what's in your /var/log/messages file for around that time?
I see the var/log folder but not the messages.log file

---

### Post by LinuxSavedMyComputer on 2011-08-12
OK. It just happened again
the message was different, but the only line i could read is "asking all processes to terminate"
I was looking at the syslog file.
Could it be kernel panic (as i think it is calledd) or a virus

---

### Post by LinuxSavedMyComputer on 2011-08-12
Found the problem  :D  
went through the kern.log

found this line
Aug 12 09:28:11 linux-Inspiron-1525 kernel: [ 8059.102356] Critical temperature reached (99 C), shutting down.

thanks for the help

---

### Post by dino99 on 2011-08-12
so is it overclocked ? Are fans working ? can it get some fresh air ? maybe too dusty.

---

### Post by LinuxSavedMyComputer on 2011-08-12
> **dino99 said:**
> so is it overclocked ? Are fans working ? can it get some fresh air ? maybe too dusty.
Might be dusty, fan or some part of the CPU might be damaged. I am not tech savvy (yet).
The computer i am using is heavily damaged. the battery can operate at 7.2% of maximum (and drains 2% charge every 45 seconds just in the BIOS settings menu) and the last 50 gigs of the hard drive are corrupted. Windows Vista couldn't boot, and the Windows XP installation disc refused to partition the hard drive. A few weeks ago i thought is was more useless as my 98 machine.

---

### Post by dino99 on 2011-08-12
into the bios you might see something to force the battery to be completly discharge, do it its necessary before recharging it. 

About the hdd, boot on a livecd and run gparted (or so) to look at partition(s) errors (but be carefull to not erase your data, take time to understand what you are doing, if you cant then dont do)

---

### Post by LinuxSavedMyComputer on 2011-08-12
The battery itself is damaged
I already partitioned the HDD when i installed ubuntu

---

### Post by Evilware on 2011-08-12
remove the battery and just use the a/c adapter

---

