---
title: "Bad sectors"
date: 2009-11-02
forum: General Help
---

### Post by blueskyatfero on 2009-11-02
So,
Unbutu 9.10 is totally freakin awsome!!!!!!! My problem is when I upgrraded to ubuntu 9.10, mmy ubuntu disk utility told me that I have a disk health problem, ad when I furth investigated this issue in ythe disk utility it said I had many bad sectors to the tune 0f 65 or so. Long story short I used the microsoft DU to try to recover the sectors and surprize, surprize I now have 74 bad sectors! The thing is I'm starvin like marvin in school on scholarships and I dont really have the money for a new HD. A guy I know said in short I could use a GPARTED live disk andc just format the whole drive, and that may or may not solve the problem,Im not super bummed about that since Ubuntu if by far my preference and also since microsoft has been raping me since i got this computer with constant issues in vista. I guess what Id like to know is, should I A) follow the sugestion, or B) do nothin and wait tell it fails. I mean how bad is this issue?

---

### Post by alphaniner on 2009-11-02
There is a bug in the partitioning tool that causes 'false positives' regarding bad sectors.  I suggest you figure out the manufacturer of your HDD and download their diagnostic tool.

---

### Post by P4man on 2009-11-02
No amount of formatting or chkdsk-ing is going to solve this. Your drive is dying, its that simple. 

I imagine the bad sector count is in fact what smart monitoring tools (palimpsest in the case of ubuntu 9.10) report as relocated sector count? If so, most drives have 100 or 200 spare sectors. They automatically remap bad sectors to spare ones. Once you exceed the spare count, data loss is inevitable. 

Id say keep using it as long as you make backups regularly and accept the fact it can die any moment and/or start producing read/write errors. also keep in mind it can silently corrupt your data. Meaning if each day you overwrite your previous backup you may end up with no usable backup.

The sensible solution is replacing the drive, but its your money and your data, so you decide.

---

### Post by P4man on 2009-11-02
> **alphaniner said:**
> There is a bug in the partitioning tool that causes 'false positives' regarding bad sectors.  I suggest you figure out the manufacturer of your HDD and download their diagnostic tool.

There is such a bug, but that one gives negative readings or thousands of false positives. A small number of bad or relocated sector count like the OP gave, and the number increasing and confirmed by windows utilities means he has a real problem and palimpsest got it right.

---

### Post by bodhi.zazen on 2009-11-02
> **p4man said:**
> no amount of formatting or chkdsk-ing is going to solve this. Your drive is dying, its that simple. 

I imagine the bad sector count is in fact what smart monitoring tools (palimpsest in the case of ubuntu 9.10) report as relocated sector count? If so, most drives have 100 or 200 spare sectors. They automatically remap bad sectors to spare ones. Once you exceed the spare count, data loss is inevitable. 

Id say keep using it as long as you make backups regularly and accept the fact it can die any moment and/or start producing read/write errors. Also keep in mind it can silently corrupt your data. Meaning if each day you overwrite your previous backup you may end up with no usable backup.

The sensible solution is replacing the drive, but its your money and your data, so you decide.

+1

> **p4man said:**
> there is such a bug, but that one gives negative readings or thousands of false positives. A small number of bad or relocated sector count like the op gave, and the number increasing and confirmed by windows utilities means he has a real problem and palimpsest got it right.

+1

---

### Post by alphaniner on 2009-11-02
I reread the OP and I guess you're right about his situation, I find the post a bit difficult to follow.  But for the record, bug reports have also been filed where only 10's of bad sectors were found.

---

### Post by P4man on 2009-11-02
> **alphaniner said:**
> I reread the OP and I guess you're right about his situation, I find the post a bit difficult to follow.  But for the record, bug reports have also been filed where only 10's of bad sectors were found.

And have these been verified to be false positives using other smart monitoring tools (and not a chkdsk) ? So far Ive only seen values that are obviously wrong (negative, or 65500 and the like) but if credible looking values are also suspect to this bug Id like to learn it.

---

### Post by alphaniner on 2009-11-02
Regarding the OP's situation specifically, like I said I had trouble understanding his post.

But about the issue in general, following is a post from [https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/438136)

> 
Yup, same problem here. Seagate 1500.11.

CHKDSK /R reports no problems. Nor does SeaTools.

Palimpsest reports 55 bad sectors.

I've seen several other instances where people had bad sectors in the 1s, 10s and 100s as well, but none of them confirmed that they tested with another tool.

---

### Post by P4man on 2009-11-02
Thanks for that. But Im still reluctant to accept that as a bug confirmation. I dont know if seatools tests smart data, or just does read/write tests. With 55 relocated sectors it would still pass any read/write tests. 

And even if it checks smart data, perhaps seatools would  not consider it a problem until it reaches a higher number. Keep in mind if their own program reports a failure they'd likely have to replace it under warranty , so seatools may OK the drive until it almost ran out of spare sectors, where as palimpsests warns a lot earlier. Hard to tell. Ill try seatools on one of my seagate drives later to test. But for now I would be very reluctant to blame this bug for any reported drive failings that is not clearly bogus. Its not like palimpsest is utterly broken, it works just fine on the 7 hdds ive tried it on.

edit: seatools does read smart monitoring, but my drive has zero relocated sectors so obviously it okay's it and I dont know what it would do with 55...

---

### Post by blueskyatfero on 2009-11-02
Thanks for the info and sorry for the garbled post I was in a rush to get to my differential equations class. Well I was wondering then if I chose to replace my HD with a SSD would there be any issues  as pertaining to just doin a clean install with Ubuntu 9.10? Driver incompatibility so on...? Please excuse me I'm a newbie with computers.

---

### Post by P4man on 2009-11-02
> **blueskyatfero said:**
> Thanks for the info and sorry for the garbled post I was in a rush to get to my differential equations class. Well I was wondering then if I chose to replace my HD with a SSD would there be any issues  as pertaining to just doin a clean install with Ubuntu 9.10? Driver incompatibility so on...? Please excuse me I'm a newbie with computers.

You dont have money for a hdd but you'd consider buying an SSD? have you checked the prices of these things?

Anyway, no there wouldnt be any problem. There are tweaks to be done to ext4 apparently to improve performance and reduce wear, but nothing would be required to make it run. Still Id think twice before spending a lot of money on a tiny disk.

---

### Post by blueskyatfero on 2009-11-02
ya well if I'm gonna start savin up now would be the time before the holidays hit, no since half stepping, than for all the help

---

### Post by blueskyatfero on 2009-11-02
Thanxs, your right i hadn't checked the prices as compared to the amount of disk space.

---

### Post by kkady32 on 2009-11-07
i have the same issue :bad sector
i download Hiren's Boot CD v.10.0 and run HDDRegenerator and this repair problem.
now,message from palimpsest is :'disk is healthy'

---

