---
title: "Problem using cpio to clone root partition"
date: 2010-01-06
forum: General Help
---

### Post by dgtangman on 2010-01-06
I just finished copying a bunch of partitions from an old hard drive to my bright, shiny new 1-TB drive, and I ran into all sorts of failures booting from the new drive. To copy drive-to-drive, I mounted the existing partition as /mnt and the new partition as /new and then (as root) executed

    [FONT=Courier New]cd /mnt[/FONT]
    [FONT=Courier New]find . -depth | cpio -pdm /new[/FONT]

This procedure has worked well for me in the past, but this time I found that all the directories on the new partition were owned by root. I eventually fixed the problem by erasing the new partition and repeating the copy with

    [FONT=Courier New]cp -pr /mnt /new[/FONT]

which seems to work; at least the system is running and I have encountered no further errors.

Can anyone tell me why the [FONT=Courier New]find[/FONT] & [FONT=Courier New]cpio[/FONT] method failed? It strikes me as exceedingly strange that all the files got the same ownership on the new partition as they had on the old partition, but all the directories were left owned by root. My understanding was that the "-depth" option to [FONT=Courier New]find[/FONT] caused it to list directories after their contents, so that [FONT=Courier New]cpio[/FONT] would set their modification times, ownership, and permissions after the files within each directory had been copied. That does appear to be how "-depth" operates, but it does not appear to be how [FONT=Courier New]cpio[/FONT] works. Help?

---

### Post by rnerwein on 2010-01-06
hi 
use the -print option this will keep the owner and group even when you copy the file as root
find . -depth -print | cpio -pdm -B --preserve-owner /home/new_dir
-B is for greater blocksizes.
by the side (i prefer cpio too) see: [http://www.gnu.org/software/cpio/manual](http://www.gnu.org/software/cpio/manual)
and see what else you can do with this mighty command
ciao

---

### Post by dgtangman on 2010-01-07
I'm even more baffled than previously. The [FONT=Courier New]cpio[/FONT] installed with 9.10 on my system is GNU cpio 2.10; it does not like "--preserve-owner", which its documentation claims to be its default behavior. That is consistent with my recollection of earlier versions of [FONT=Courier New]cpio[/FONT] that I have used in times past. Specification of "-print" on the [FONT=Courier New]find[/FONT] command does nothing in the absence of other actions, since "-print" is the default action.

Further experimentation has determined that omitting the "-depth" option from [FONT=Courier New]find[/FONT] yields something a great deal closer to my expectations - the permissions and ownership of created directories are copied from the source directories. The modification date on the created directories is not that of the source directories, despite the presence of the "m" option in the [FONT=Courier New]cpio[/FONT] command, which is meant to preserve modification times, but that appears to be harmless.

Why this has changed is unclear to me. If anyone can clarify, it would be much appreciated.

---

### Post by gmork123 on 2010-01-24
I have the same experience on restoring an 8.04 ubuntu system with cpio 2.9

This find etc command used to work for me also in the past (looks like it in my notes anyway). 
I did not have the time to investigate it in detail, but it looked like it are mostly first/second(?) level directories which are wrong.

I fell back to rsync.

But thanks for the skipping the depth argument hint.

---

