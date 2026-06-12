---
title: "Slow resume from standby"
date: 2010-08-02
forum: General Help
---

### Post by fizikz on 2010-08-02
I'm running Ubuntu Netbook Edition 10.04 on an Acer Aspire One with the old and slow SSD upgraded to a faster one by SuperTalent. The only problem I've noticed is that when resuming after standby, the startup is quite slow, much slower than the bootup time. In the logs, I've found these messages that seem to correspond to the delays: 

```
Aug  2 11:39:48 ssao kernel: [ 7110.000450] ata2: lost interrupt (Status 0x58)
Aug  2 11:39:48 ssao kernel: [ 7110.000674] ata2: soft resetting link
Aug  2 11:39:48 ssao kernel: [ 7110.209182] ata2.00: configured for UDMA/100
Aug  2 11:39:48 ssao kernel: [ 7110.209224] ata2: EH complete
Aug  2 11:40:19 ssao kernel: [ 7141.000394] ata2: lost interrupt (Status 0x58)
Aug  2 11:40:19 ssao kernel: [ 7141.121160] ata2: soft resetting link
Aug  2 11:40:19 ssao kernel: [ 7141.293791] ata2.00: configured for UDMA/100
Aug  2 11:40:19 ssao kernel: [ 7141.293833] ata2: EH complete
```

I've read some bug reports on this type of error but I haven't found any solutions yet. Any ideas?

---

### Post by fizikz on 2010-08-03
When resuming from standby, the hard drive light stays on constantly and the system stays frozen for 1-2 minutes. A cold start takes less time than that. I could understand the hard drive light being on if I were resuming from hibernate, but not from standby. Any tips at all?

---

### Post by fizikz on 2010-08-10
Now, I've noticed that these errors don't just happen when resuming from standby. The same errors I posted above came up after a fresh boot, and also sometimes happen randomly while using the system. Or at least it seems random to me, I haven't found a cause yet. It's very annoying! If anyone knows what's going on please let me know!

---

### Post by Wtower on 2011-02-16
Have you found any solution to that I wonder. I have the same issue here on one netbook. Very annoying indeed.

---

### Post by fizikz on 2011-02-16
I have since upgraded to Ubuntu 10.10 on the netbook. So far I haven't noticed the freezing issue during normal use, but I can't say for certain about the resume from standby as I haven't used that function for some time. It is a very frustrating issue and I hope someone finds a solution...

---

### Post by nogasbiker on 2012-05-29
> **fizikz said:**
> I have since upgraded to Ubuntu 10.10 on the netbook. So far I haven't noticed the freezing issue during normal use, but I can't say for certain about the resume from standby as I haven't used that function for some time. It is a very frustrating issue and I hope someone finds a solution...Still there, surprisingly.  Running on a newly installed and updated 10.04 on a HP/Compaq Evo lappy.  Also spends a loooong time in standby with the disk light on solid.

Might as well start using hibernate, as I want LTS so I can't go to 10.10

---

### Post by fizikz on 2012-05-29
> **nogasbiker said:**
> Still there, surprisingly.  Running on a newly installed and updated 10.04 on a HP/Compaq Evo lappy.  Also spends a loooong time in standby with the disk light on solid.

Might as well start using hibernate, as I want LTS so I can't go to 10.10

This problem went away some time ago, but I don't know what solved it. I'm now running 12.04, but I don't think I had the problem with 11.04 or 11.10. If you want to stick to LTS, you could consider 12.04.

---

