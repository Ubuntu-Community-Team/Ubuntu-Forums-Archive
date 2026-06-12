---
title: "Recover Ext4 Partition After Crash"
date: 2010-10-13
forum: General Help
---

### Post by crazybilly on 2010-10-13
Last night, I was moving some very large data files (VirtualBox hard drive images) around my home partition (ext4) in preparation to upgrade from 10.04 to 10.10. 

I left my computer for a minute and came back to a kernel panic--the screen was off, the computer unresponsive and the hd light was flashing regularly.

This isn't that big of deal, I thought, so I turned the power off and rebooted. And that when I found out the crash had hosed my entire /home.

I tried booting into a recovery shell w/o mounting /home (also known as /dev/sda5) and running [HTML]fsck.ext4 -y /dev/sda5[/HTML], but it seemed to stall part way through--it just sits w/o spinning the hard drive at all.

Maybe I should just let it run? I'm running a badblocks check on it now--started last night, and for 6 hours while I slept and was 30% done when I woke up.

Any suggestions on where to go next?

The good news is that most of the data on there was disposable. The bad news is that a few random things were not. Running some sort of recovery tool to suck the data I need out would be time-consuming and tedious, but probably worth it if it comes to that.

Thoughts?

---

### Post by crazybilly on 2010-10-15
For the record, I ended up putting in the Lucid live CD I had laying around and running the following in a terminal to fix things:

```
fsck.ext4 -y /dev/sda5
```

That did it. Interestingly, doing the same from a recovery console did not. I'm not sure what the difference is/was--from the root recovery console I made sure /dev/sda5 was unmounted.

Regardless, I got all my data back. Woot!

---

### Post by Zill on 2010-10-15
crazybilly:  Glad you got things working again.  :-)

Top-tip - It is *always* good to have daily data backups as you never know when a hdd will fail.  This is even *more* important when you are upgrading the OS. ;-)

---

### Post by crazybilly on 2010-10-15
The funny thing is, I borked stuff whilst getting my files organized so I COULD back them up (after I recovered, I ended up deleting about 30GB of unneeded data, mostly old VirtualBox images--didn't want to waste space back that crap up).

Ah, the irony. ;)

---

