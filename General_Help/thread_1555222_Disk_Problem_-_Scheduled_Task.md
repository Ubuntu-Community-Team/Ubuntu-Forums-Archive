---
title: "Disk Problem - Scheduled Task?"
date: 2010-08-17
forum: General Help
---

### Post by alang184 on 2010-08-17
Hello. I hope I am posting this in the right place.

I'm using a Dell Inspiron 6400 laptop. My hard disk suffered some physical damage, seemingly from a knock. After this, every time I ran Windows' chkdsk, the disk mechanically kept getting stuck at the same point near the end of the disk (the sound is a bit like when a winding cassette tape reaches the end of the tape, and gets stuck with a repetitive noise). So I partitioned off this section where it gets stuck, and reinstalled Windows & Ubuntu.

It was working fine for a few weeks, but now, if the disk is left idle for around 5 minutes, it suffers this same problem where it gets mechanically stuck and the CPU is hit with 100% activity. If, within around 1 second, I create some disk activity (such as browse to a folder not already cached), then it recovers. But typically, I'm not quick enough and it gets stuck, requiring a force-shutdown with my laptop power-button.

So I'm wondering does Ubuntu have some kind of background disk checking or seeking of any kind? I've considered that the disk may be attempting to spin-down, but I think spin-down is not enabled in my Ubuntu (all the lines in the file /etc/hdparm.conf are commented out with '#').

The first thing people will say is "Get a new laptop! Back up data". Yes, I've backed up the data, and am preparing to get a new laptop soon. But for another few weeks, I need to keep this thing working.

Thank you in advance for any help.

---

