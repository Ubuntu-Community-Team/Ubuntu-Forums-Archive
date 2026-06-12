---
title: "Recurring problem"
date: 2011-02-28
forum: General Help
---

### Post by widiot on 2011-02-28
I get the same problem with every version of linux that I use. I am sure its a hardware problem/conflict and was wondering if its possible to fix. In the past week I have installed ubuntu 10.10,and kubuntu and every time i get the same problem. My resources are getting eaten up by an error that just repeats infinately. Even during boot up the error is visible on screen. My system boots up,albeit slowly and I can use it. The error is something to do with my HD. I have tried diffferent partitions, different distros  yet every time I get exactly the same error. Using Ksystemlog shows what is happening....

2011-02-28 17:20:04    ata4.00    configured for UDMA/100
2011-02-28 17:20:04    ata4    EH complete
2011-02-28 17:20:04    ata4.00    exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6
2011-02-28 17:20:04    ata4    hard resetting link
2011-02-28 17:20:05    ata4    SATA link up 1.5 Gbps (SStatus 113 SControl 300)
2011-02-28 17:20:05    ata4.00    configured for UDMA/100
2011-02-28 17:20:05    ata4    EH complete
2011-02-28 17:20:05    ata4.00    exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6
2011-02-28 17:20:05    ata4    hard resetting link
2011-02-28 17:20:05    ata4    SATA link up 1.5 Gbps (SStatus 113 SControl 300)
2011-02-28 17:20:05    ata4.00    configured for UDMA/100
2011-02-28 17:20:05    ata4    EH complete
2011-02-28 17:20:05    ata4.00    exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6
2011-02-28 17:20:05    ata4    hard resetting link
2011-02-28 17:20:05    ata4    SATA link up 1.5 Gbps (SStatus 113 SControl 300)
2011-02-28 17:20:05    ata4.00    configured for UDMA/100
2011-02-28 17:20:05    ata4    EH complete
2011-02-28 17:20:05    ata4.00    exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6
2011-02-28 17:20:05    ata4    hard resetting link

This error just continues for ever and as the faulting module keeps restarting Im worried about the damage its likely causing to my HD(the light just flickers constantly)

Is there any way to fix this or will I have to stick to windows until I get myself some new hardware?
Any help gratefully received

---

### Post by widiot on 2011-02-28
Not really a solution,but I have found a fix to this problem. If I go to my bios and change my sata setting from IDE to RAID then I no longer have a problem with the constant interrupts:popcorn:. The only problem with this is I use a dual boot system and cannot boot windows using the RAID setting:confused:

---

