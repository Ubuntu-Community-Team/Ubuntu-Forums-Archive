---
title: "Boot failure 9.10 ubuntu"
date: 2009-12-07
forum: General Help
---

### Post by EdWh on 2009-12-07
Hi All, 

I have two machines both upgraded from 9.04 to 9.10 latgest release. 
Today one machine will not boot.   The machine was running the normal file check after 30 reboots and posted that it was mounting the splash screen and it hung.   Notice that maintenance shell has started then opened prompt as - root@ed-deskdtop:~# with flashing cursor.  Machine is still hung at this point.  I believe I need to get rid of splash screen but am not sure, please be concise as I hardly use terminal, but can follow instructions.  This notice is being posted on second machine still o.k.   Thanks.   Ed.

---

### Post by cariboo on 2009-12-07
I would suggest you do a hard shutdown, then boot from the Live CD and run fsck on the partition.

---

### Post by EdWh on 2009-12-07
> **cariboo907 said:**
> I would suggest you do a hard shutdown, then boot from the Live CD and run fsck on the partition.

Thanks for info, actually after rebooting and it came back to same command prompt, and reading above it I found it said to run fsck manually which I did and it found several error and asked if I wanted to fix which I did and it reboot correctly to desktop.    Thanks for all the help.   I do not use command prompt very much as it almost never needs manual work.   Ed.   
Merry Christmas.

---

### Post by burton247 on 2009-12-07
Mine died during the standard system check but fsck fixed it up nicely. None of my computers have ever failed any of these before though

---

### Post by EdWh on 2009-12-12
Hi burton247

Since my computer actually gave me a root prompt and reading above told me to run Fsck it is apparent the designers have run into the problem in the past but it would be nice to let us know about some of these glitches so we could be prepared.  Nothing like a good surprise.   Merry Christmas and thanks for the reply.      Ed.

---

