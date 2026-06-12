---
title: "Risk in Ubuntu damaging files on an NTFS partition?"
date: 2011-01-13
forum: General Help
---

### Post by niblettes on 2011-01-13
This might be a really dumb question, but I saw an article that cautioned against accessing files with Ubuntu that are stored on NTFS partitions.  The warning was that doing so over time can increase the risk of damaging those files.

Is there any truth to this, or is it complete nonsense?

---

### Post by piquat on 2011-01-13
Plenty of people have shared NTFS data partitions to share things between Linux and Windows.  I do.  It's never given me a problem, albeit I've only been doing it for a few months.

---

### Post by elroulade on 2011-01-13
never heard of something like this before.

p.s. Im using ubuntu to access files on an ntfs partition every day and never had a problem.

---

### Post by veggen on 2011-01-13
I know of that story. It used to be true (not just for Ubuntu, but any Linux). The NTFS drivers weren't the best when it came to writing to disk (reading was ok even back then). Nowadays, I think it's pretty safe to do whatever you wish with your NTFS partition from Linux. As others, I've been doing that every single day since installing Ubuntu (about a year and a half ago).

---

### Post by oly on 2011-01-13
Its pretty safe my ubuntu install is on a ntfs partition and i use that on a daily bases for work, and still read and write the files from the windows side as well so yeah i would say its pretty safe.

---

### Post by West201 on 2011-01-13
I don't believe that article :confused:. Do you have the link ? :)

---

### Post by James78 on 2011-01-13
I use NTFS all the time with 0 issues. That did used to be the case when driver support for NTFS was in its infancy, but that's not really the case anymore. NTFS support is really good now.

---

### Post by Mark Phelps on 2011-01-13
> **niblettes said:**
> ...Is there any truth to this, or is it complete nonsense?

There IS truth to it ... and it is NOT complete nonesense.

The most common case of data corruption is when folks automount NTFS OS partitions, do writes to them, and then (for some unknown reason), do unclean shutdowns.

Also, it seems to affect Vista/Win7 OS partitions much more than XP OS partitions.  It does not seem to affect purely data partitions.

---

### Post by oldfred on 2011-01-13
To add to Mark Phelps comments.

I have used NTFS for a couple of years without issue. But I avoid writing into windows system partition. Users make mistakes. With Ubuntu you have total access to all the files that windows normally hides. If you do not know what your are doing or even if you do, you can accidentally click incorrectly, and then you can move or delete a critical windows system file. 

Also users hibernate in windows, then in Ubuntu write into the windows system, corrupting the hibernation.

It is much better to set windows system partition as read only and create a shared NTFS partition for any data you may want from either system.

---

### Post by piquat on 2011-01-13
That's nice to know.  I use a separate data partition but I had no idea I probably should keep my fingers out of the windows partition itself.

Thanks!

---

### Post by srs5694 on 2011-01-13
I'll add this: I know of no serious scientific study of the issue. To do such a study, you'd need to set up a bunch of computers running Linux, another bunch running Windows, and run a series of scripted operations including reads, writes, clean and unclean shutdowns, etc., then check each filesystem for damage and see whether there's a difference between the two OSes.

Anecdotal evidence, as several here have presented, is not very useful, except perhaps to get a general feel for how big the danger is in vague but absolute terms -- but not how it differs from the danger of using a disk in Windows. That is, a dozen people might post that they've had no problems, but if you increase the sample to twenty, maybe a problem would crop up; and that might represent a five-fold increase in the risk vs. using the drive from Windows. (I'm pulling these numbers out of thin air, of course; don't take them seriously.) An exception would be if somebody has found a repeatable bug that causes data loss; such a bug could be valid even from just a single report (if the reporter is to be trusted).

There are lots of testimonials that the NTFS-3g drivers (which Ubuntu uses for NTFS access) are fairly robust; however, as oldfred has said, Linux doesn't recognize the standard NTFS security features that Windows uses, which makes it easy to accidentally damage the Windows installation. For that reason alone, I recommend that people create a separate data-exchange partition and use that for data exchange, rather than writing directly to the Windows C: drive. Add to that the possibility that the NTFS-3g drivers are less reliable than the Windows NTFS drivers, even if NTFS-3g is fairly reliable, and being cautious makes even more sense. I don't know that NTFS-3g is less reliable than Microsoft's own NTFS drivers, but it's possible, and it seems unlikely that NTFS-3g is more reliable, so playing it safe seems tobe in order.

---

### Post by niblettes on 2011-01-13
Thanks everyone.  It sounds like there may have been some potential danger in early version of Linux, but not in current version.  It also sounds like the only danger now is user error (inadvertently allowing Linux to modify something Windows doesn't want modified).

That solves it for me.  I can know confidently continue using Unbuntu on the contents of my data partition.

---

