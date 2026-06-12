---
title: "Display reverts to low resolution"
date: 2009-10-30
forum: General Help
---

### Post by Richard Hunt on 2009-10-30
I installed Intrepid 8.10 on an old PC a few weeks ago. It is an Athlon XP 1800+ cpu with 512 MB RAM and 100GB Maxtor HDD.  The graphics card seems to be S3 ProSavage.  The setup also uses an Aten KVM switch so I can access my main PC from the same console.  Keyboard mouse and screen work fine.

Installation was fine, and the display was of high resolution. After a few days on start-up, I got the message that the graphics were not supported and it reverted to low resolution and higher resolution was not supported under Screen Resolution.

I decided that upgrading to 9.04 might resolve the issue, and indeed it did and ran for several days with no problem.  However today on starting the system it has reverted again to low resolution, and I can see no access to screen settings to check what can be done.

Update manager reports 9.10 now available, which no doubt will resolve the matter again, but for how long?  

I have searched the Forum but cannot find anything directly relevant.  It seems XORG may be involved but my knowledge of what and how to make changes is nil.

It is possible also that the KVM switch is interfering with the boot process (although it did not do so for several days).  I cannot prove this.

Does anyone have any ideas, suggestions for me to try.  Please assume little or no knowledge of the system in replying.  I am a learner.

Thank you.

---

### Post by P4man on 2009-10-30
It is the KVM switch for sure. If you google for ubuntu and KVM you will find countless posts and blogs describing the same issue. A cursory glance over them has not given a definite solution Id recommend, but Im sure if you look a bit harder you'll find one. Dont hesitate to ask for help if you find something tho. Or perhpas someone else can post a solution, but im not a xorg.conf specialist either :s

---

