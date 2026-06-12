---
title: "Resizing root partition on working install"
date: 2009-11-23
forum: General Help
---

### Post by memilanuk on 2009-11-23
Hello all,

I have an older PC pulling duty as a home file-server running Ubuntu 8.04 Server LTS.  Three hard drives - one 13.8GB PATA drive with 12.5GB partition for /, the remainder for swap, and two 500GB SATA drives in a software RAID 1 config mounted under /srv.  Nothing hugely mission critical, other than its running BackupPC and I'd sure hate to have to redo the initial full backup from my Windows desktop (hundreds of gigabytes) ;)

For a bare-bones server install, 12+ GB is obviously pretty under utilized.  I have an urge to resize that main root partition a bit smaller, and use that 'extra' space in another manner.

What would be the best way to go about non-destructively resizing the root partition of an existing install?  I'm looking into different options - booting from an install CD and resizing the partitions, but I'm not sure if that would nuke the info stored on the original partition or otherwise hose the boot sector...  the other options I'm looking at include SystemRescueCD or RemasterSys.  So far it looks like SystemRescueCD should be able to do the job without any headaches... but I'd appreciate hearing from anyone else who has done a similar evolution.

Thanks,

Monte

---

### Post by lmarmisa on 2009-11-23
Hi Monte,

you tell that 12+ GB is too big partition and you want to reduce it!!.

I misunderstood you when I read your comment the fisrt time and thought just the opposite.

I don't how your plan to use that 'extra' space in another manner. If your idea is to use this space inside Ubuntu, may be you don't need to modify your partitions. A simple symbolic link could be the solution.

In any case, my experience with GParted for changing the size of partitions has been good. But I think that a previous backup would be a prudent decision.

Best regards,

Luis

---

### Post by prshah on 2009-11-23
> **memilanuk said:**
> I'd appreciate hearing from anyone else who has done a similar evolution.

I haven't done this exactly; but I have resized my root partition from 9GB to 15GB when I wanted to install Kubuntu side-by-side with my Gnome install.

I used a live CD, shrank the partition before the "/" partition, then expanded/moved the root partition into the free space.

However, I do suggest a good backup, because I had a nasty gparted experience once before (entirely my fault).

Resizing the partition should not cause any change to the boot sector, etc. Even creating another partition BEFORE the root partition should not cause a problem; the partition numbers remain the same.

Caveats: Obviously, I don't expect you to risk your install/data on my word. I would suggest you wait for further ratification. You do this at your own risk. My caution stems from the differences between your requirement and my actions: Eg you're using server edition, I was using desktop, RAID vs single drive, etc.

---

### Post by memilanuk on 2009-11-24
Thanks for the feedback!

What I had in mind was this:

Of the original 13.something GB hard drive, about 1.4 or 1.5GB was swap, and the remainder 12.2GB partition had / mounted on it.  Of that maybe just a little over 1GB was actually in use.  While there is always a potential for /var or /tmp to fill up with logs or junk, that would have to be a *lot* of logs for a small home file server used as an overgrown NAS/backup server.

So... being the sort who can't leave well enough alone :rolleyes: I decided I had to do *something* with that extra space ;)

What I have in mind is splitting the drive into three 4GB partitions with the remainder as swap.  The working, known-good Ubuntu 8.04.3 LTS server install will remain on the first partition, and for the most part continue to do what it does best: work.  The other two partitions will become my test bed partitions for other releases of Ubuntu, or other distributions.  I know I have things up and working in Ubuntu 8.04, now I can test other options like CentOS 5.4 or Debian Lenny  or openSuSE 11.2 or Ubuntu 10.xx Lynx before committing fully (if at all).  The data drive(s) should still show up as a RAID array in the other operating systems (its a nice theory; we'll see how well that idea works in actual practice) or I can just leave them untouched until I'm comfortable making that move.

This configuration should have the added bonus of the 4GB 'system' partitions being just about exactly the max size allowed by RemasterSys, so I hope to have some options there.

Why not play with the other operating systems in Virtualbox (which I have on my desktop)?  Well... I have, but there always seem to be some interesting wrinkles that arise when faced with actual installs on real hardware that make life... interesting ;)

FWIW, the route I took was to burn a SystemRescue CD and boot from that, then use GParted to resize the partitions as necessary.  Appears to have worked nicely - Ubuntu 8.04.3 LTS back up and running ;)

---

