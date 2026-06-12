---
title: "Lucid- Could latest 2.6.32-34  kernel cause hard disk errors?"
date: 2011-08-26
forum: General Help
---

### Post by emarkay on 2011-08-26
There were a few bugs in that one and I am suddenly getting the following errors as the disk goes "thunk" and the access lamp illuminates:

[15992.248036] ata1: soft resetting link
[15992.441207] ata1.00: configured for UDMA/133
[15992.457848] ata1.01: configured for UDMA/133
[15992.457891] ata1: EH complete
[16028.000057] ata1: lost interrupt (Status 0x50)
[16028.000142] ata1: soft resetting link
[16028.192915] ata1.00: configured for UDMA/133
[16028.209859] ata1.01: configured for UDMA/133
[16028.209869] ata1.00: device reported invalid CHS sector 0
[16028.209891] ata1: EH complete
[16069.000054] ata1: lost interrupt (Status 0x50)
[16069.000140] ata1: soft resetting link
[16069.192986] ata1.00: configured for UDMA/133
[16069.209840] ata1.01: configured for UDMA/133
[16069.209849] ata1.00: device reported invalid CHS sector 0
[16069.209869] ata1: EH complete

The disk I think is doing this is sdb, a Maxtor PATA 6B200R0.
How do I confirm which disk is "ata1"?

The disk is not mounted, but it is still affecting the system when it does this. 
What's strange is I was getting hard reset lockups with an HSM Violation for the past couple of days, now it's not locking up...

There's a Kernel / wontfix bug on this with an interesting quote "Problem persists in Lucid. Random 30 second lock ups and resuming..."
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/397096](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/397096)
Anyone have more info??

---

