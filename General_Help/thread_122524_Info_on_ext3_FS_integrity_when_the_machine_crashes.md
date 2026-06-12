---
title: "Info on ext3 FS integrity when the machine crashes"
date: 2006-01-27
forum: General Help
---

### Post by mabster on 2006-01-27
My machine has been overheating (hence rebooting) a fair bit recently and I've started to wonder about what this is doing to my FS integrity.  I've noticed cases where particular files are now directories when I next start up, or files are locked (and ls can name them but not tell you any of their attributes).

Is there somewhere I can find information on this?  I've heard people mentioning using fsck but that tool doesn't appear to like to work on mounted partitions (how do I unmount root and still have a running system?!).

---

### Post by Burke on 2006-01-27
"(how do I unmount root and still have a running system?!)."
You could use a LiveCD.

I think ext3, being a journalled FS, is reasonably good at not screwing up when it crashes. That whole file->dir thing seems to be a little odd, but I highly doubt you'll ever find your whole FS corrupted.

Also, I think fsck runs automatically on boot when you system crashes... do you see some progress bar slowly making its way across your screen on boot?

---

### Post by thespazzz on 2006-01-27
I hate to tell you this but I don't think this is the fault of EXT3 or any other file system.  I had similar problums with NTFS under Windows a while back and it turned out to be a combination between a bad Mainboard and a partaialy defective hard drive.

I'd back everything up off of that drive and run some diagonostics on it and find out what the root cause of your overheating/rebooting is.  You may find if you fix that and it may fix your file system errors.

---

### Post by mabster on 2006-01-28
I'm looking into the overheating thing at the moment -- it seems to be a common issue with my laptop brand (Dell Inspiron 5150) :(.

I was running WinXP on this laptop as of two weeks ago and I never had this issue (I think the machine only overheated twice or so and both times the filesystem checked-out).  NTFS.  By diagnostics do you mean fsck?  Is there anything else I can run?

As to fsck running automatically on boot:  I don't think so.  I haven't seen it run when the machine starts up after a reheat.  I have, however, seen it run "after 30 mounts" with no problems detected (in fact, the last time this ran was about a day ago).  Is it advisable to get fsck to always run?  I've heard that ext3 stores a flag if it was unmounted so the check is really quick if the machine unmounted properly?  How would I go about setting fsck to run during boot?

Thanks!

---

### Post by dcstar on 2006-01-28
[QUOTE=mabster]My machine has been overheating (hence rebooting) a fair bit recently and I've started to wonder about what this is doing to my FS integrity.  I've noticed cases where particular files are now directories when I next start up, or files are locked (and ls can name them but not tell you any of their attributes).

Is there somewhere I can find information on this?  I've heard people mentioning using fsck but that tool doesn't appear to like to work on mounted partitions (how do I unmount root and still have a running system?!).[/QUOTE]
Have a look here for different performance/integrity options:

[http://ubuntuforums.org/showthread.php?t=107856](http://ubuntuforums.org/showthread.php?t=107856)

---

### Post by mabster on 2006-01-28
I just realised this may be an ext2 problem (though I've applied those ext3 tweaks to my partition since on my laptop, less file access means less heat ;).

My root mount is set an ext3 partition.  My /home/ is mounted to another partition with ext2 (so that that drive may be accessible from Windows when I get around to installing the ext2 Win driver).  With a bit of thinking about files that have had trouble (Azureus, Mozilla bookmarks, etc.) they all appear to be files that would exist in my home folder.

I might think about moving my home folder stuff back to the ext3 partition and just keeping them there for now and see if that helps with this issue (I assume that ext2 wouldn't like the machine being killed half-way through disk access).

And oops, completely forgot I had done that ;)

Thanks guys!

I still wouldn't mind any info on getting fsck to run properly on startup ;) !

---

### Post by dcstar on 2006-01-28
[QUOTE=mabster]
.......
I still wouldn't mind any info on getting fsck to run properly on startup ;) ![/QUOTE]
Do a forum search, there are many posts on running it on startup.

---

### Post by mabster on 2006-01-28
But the search buttons soooo far away! ;)

I'll have a search, thanks for all the info!

---

### Post by briancurtin on 2006-01-28
[QUOTE=mabster]I'm looking into the overheating thing at the moment -- it seems to be a common issue with my laptop brand (Dell Inspiron 5150) :(.[/QUOTE]
what are your processor specs?

i have an HP laptop that used to overheat a ton when i was newer to ubuntu and linux and general (overheated all the time in windows too), and the i686 kernel solved the problem for me. my laptop is an absolute beast, so i should have looked into that kernel much earlier, but it was a newcomer mistake

---

