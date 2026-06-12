---
title: "fsck , a flat cmos battery and failed boots"
date: 2010-02-24
forum: General Help
---

### Post by jman6495 on 2010-02-24
So , hi all , my cmos battery is dead , not worrying that much about it but the problem is ubuntu , it has trouble booting thanks to fsck , there is a bug here [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/510403](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/510403)
but i cant boot , i get the following error

 # Superblock last mount time is in the future

and i cant boot , i can get it working sometimes , with allot of work , but normaly it just fails !

i came to the conclusion that the CMOS time and date keeps reseting and so ubuntu thinks that the last time i booted was in the future (if this makes any sense) and fsck freaks ,


any help would be much appriciated 


          jman6495

---

### Post by ram2500 on 2010-02-24
I would just let fsck run, and then it should boot once it's done checking the drive. I've had a similar problem before...I think by editing fstab and setting the fsck value to "0" at the end of the drive's mount information line (I'm not really clear if this is correct, hopefully someone may elaborate if I wasn't concise) If you are faint-of-heart, I wouldn't change anything and would just let fsck run its course until you get a CMOS battery replacement. You do want fsck run from time to time, so disable fsck if and only if this is a major inconvenience.

---

### Post by Gen. Lee poor on 2010-10-31
Hi. 

I'm having exactly the same problem with a HP mininote 2133, with Ubuntu NBR 10.04. 
The battery dies on the netbook if it's not used, but then I can't boot ubuntu due to the same error (last mount time is in the future). It just seems to hang though. The error message (if I press esc from the purple bootup screen says 
"/dev/sda1: UNEXPECTED INCONSISTENCY: RUN fsck MANUALLY"

But how do I get to run it (or is it already running in the background? I can't get to a login window.

---

### Post by ZaHACKieL on 2010-12-03
I just had that issue now. My CMOS battery is almost dead I guess because most of the time my laptop starts with the factory BIOS settings so I have to change the time and Flash Module option. 

Anyway, it seems that yesterday by accident, instead of setting the time for December 2 2010 I selected December 2 2011, so today I got the "last mount time is in the future", and the error was regarding my filesystem partition. 

I first tried changing the BIOS time to the future and it booted but after login the system just hanged, so I restarted and did what the terminal says "RUN fsck MANUALLY". I think I first did CTRL+D , so anyway, it fixed the filesystem problem and after reboot I got the same message but for the home partition. Did the same fsck for that and the problem got away.

I was really scared when I saw that message but it seems that everything is working fine now =/

---

