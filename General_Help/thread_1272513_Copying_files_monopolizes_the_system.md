---
title: "Copying files monopolizes the system"
date: 2009-09-22
forum: General Help
---

### Post by P4man on 2009-09-22
Im not sure if I should file a bug for this, or not. But in both jaunty and karmic, when I move or copy large files (using nautilus, using Ext3 or 4, only 1 physical drive being used), the entire system grinds to a standstill. Well, not quite actually, *anything I/O related* grinds to a halt.

I can still spin my desktop cube at 500 or whatever FPS, zoom in and out using compiz without any stuttering whatsoever, but watching a movie becomes impossible, even browsing the web becomes painfully slow, firefox and other browsers regularly becoming unresponsive for several seconds, even typing text (like this post, while im copying 100GB) will often pause for several seconds. Launching another app, say Evolution takes forever.

It seems like nautilus copy operations have a too high I/O priority. Copying speed is good (30+ MB/s), but Id really like to trade a little bit of copying speed to enhance system responsiveness. Is there such a  thing as I/O priority ? 

FWIW, I got a dual core CPU, 2GB Ram, neither of which are really loaded.

---

### Post by P4man on 2009-09-23
No one? Is this considered normal behavior?

---

### Post by Grenage on 2009-09-23
Ahoy there!

I tried to replicate the issue, but couldn't replicate it entirely.  I set a drive to copy 30GB into a Truecrypt archive, then watched a HD movie; the movie played fine, but skipped a frame once every 5 minutes or so.

If you run Nautilus with a low nice priority, does it still occur?

---

### Post by fuzzyk.k on 2009-09-23
In my use of many other Linux systems as well i have seen the same behavior, it seems its a norm

---

### Post by fuzzyk.k on 2009-09-23
> **Grenage said:**
> Ahoy there!

I tried to replicate the issue, but couldn't replicate it entirely.  I set a drive to copy 30GB into a Truecrypt archive, then watched a HD movie; the movie played fine, but skipped a frame once every 5 minutes or so.

If you run Nautilus with a low nice priority, does it still occur?

anyone tried it ? and forgive my ignorance but how do you change the priority ?

---

### Post by P4man on 2009-09-23
> **Grenage said:**
> Ahoy there!

I tried to replicate the issue, but couldn't replicate it entirely.  I set a drive to copy 30GB into a Truecrypt archive, then watched a HD movie; the movie played fine, but skipped a frame once every 5 minutes or so.

If you run Nautilus with a low nice priority, does it still occur?

I just tried with both extreme nice settings (-20 to 19) and I can't say i notice any difference (good or bad). I did notice however, that shutting down deluge made much more difference (even though it was up and downloading at just 10Kb/s). Responsiveness is still not great, but at least bearable without deluge running.. I'll look further in to that.

---

### Post by Grenage on 2009-09-23
> **P4man said:**
> I just tried with both extreme nice settings (-20 to 19) and I can't say i notice any difference (good or bad). I did notice however, that shutting down deluge made much more difference (even though it was up and downloading at just 10Kb/s). Responsiveness is still not great, but at least bearable without deluge running.. I'll look further in to that.

I'd dabble here but it doesn't look like I'll be able to replicate it to the point where it's useful.  Let us know if you do get any closer to an answer, I've heard people complaining about it before.

I'm not aware of any tools that allow one to throttle disk transfer, but I'll take a look.

---

### Post by 3rdalbum on 2009-09-23
For the record, I do have a high "CPU wait" in the System Monitor applet when I'm ripping DVDs;  it does affect the system responsiveness.

---

### Post by etnlIcarus on 2009-09-23
I thought this was normal, across all operating systems.

---

### Post by shane2peru on 2010-01-31
My 2 cents worth.  I'm on day two for copying a 140GB disk image from one hdd to another hdd.  Started with 30mb/sec and am down to 1mb/sec, and a system that also has become slower.  I'm not using nautilus, but rather command line, and I installed bar so I could monitor the progress while it is copying.  My theory is this, since it is such a large file, and very unlikely that the File System (copying to ntfs disk in my case) has 140GB of consecutive free space, therefore in the beginning it is rather easy for the computer to 'find' the large free areas on the disk to write the data, however as it becomes filled up, it becomes more difficult for the computer to find consecutive space to write the data too, and find the chunk size to write to.  This is based on my limited understanding of how a hdd stores data, and how FAT32 especially becomes fragmented, and you are required to run de-frag.  My understanding of ntfs is less, but I'm assuming that they have not improved the fragmentation that occurred in Fat32, to such a point that it is non-existent on a ntfs system.  I believe they still have the defragmentation application in windows XP and Vista, therefore it must still be a problem, although somewhat less.  Now with ext3, ext4 and reiser I really don't understand how they write to the disk, perhaps someone can explain this to us, and shoot my theory out of the air.  That is my theory, you can take it or leave it, or even explain, modify or disagree with it all you want.  I'm sure there are more knowledgeable people than myself.

Shane

---

### Post by SuperSonic4 on 2010-01-31
What about *cp* from terminal? I find it more efficient than dolphin

---

### Post by shane2peru on 2010-01-31
> **SuperSonic4 said:**
> What about *cp* from terminal? I find it more efficient than dolphin

As a general basis yes, but for a file this large, it is different, I think it probably depends on 1.  size of the file you are copying, and 2.  size of the disk you are copying too.  I'm copying a 140GB file to a disk with 150GB free space on it, so it will fit, but because of fragmentation (see my theory above) takes forever.  Using cp doesn't allow you to see what is being done.  I installed bar, and used: bar filename > new/location/filename  and it allows me to see the speed and progress of what is going on.  Bar is not in the repos, I found it and installed it separately which is not really recommended, but I couldn't find any command line application that I could figure out how to use and do the same thing.  

Shane

---

### Post by blueshiftoverwatch on 2010-01-31
> **etnlIcarus said:**
> I thought this was normal, across all operating systems.
Same, files being copied+pasted are stored in the RAM. Since RAM is shared across the entire system and can't as far as I know be limited to X amount for certain operations I don't think theirs a way around it either.

---

### Post by shane2peru on 2010-02-03
Well, after 72 hours into copying the 140GB file the power in the house went out and the external hdd lost power, which botched the whole thing.  Being the persistent fellow I am, I defraged the ntfs drive I was copying to, and am attempting this again.  I have almost 90GB copied after only about an hour copying at 20MB/sec and seems that defragmenting the drive helped exceedingly!  Less than an hour left to finish, I'm very impressed.  

Shane


PS  - Three hours to finish the transfer!  I guess my theory of the fragmentation was valid.  FYI

---

