---
title: "Some files not copied properly"
date: 2011-02-23
forum: General Help
---

### Post by God Of Atheism on 2011-02-23
Hi,

Lately I've tried rsync for backing up my home partition to an external drive, but I've run into some problems with some flac files (there might be other problematic files though, these are the ones I know of).

The external drive is formatted in ntfs.

Now, when adding my whole music directory (within my home directory) first as a library to VLC and then copying to the playlist, some files are not playable. I discovered this at work in windows, and resaved all the flac files using ex falso to skip windows incompatible characters. The problem persisted though. I tried the same thing in VLC in Ubuntu, and got again a set of non-playable files, partly, but not completely, overlapping the set of files that were not playable in windows. The original files (on my internal drive) are playable in VLC in Ubuntu.

Any idea what to do (except to go back to cp instead of rsync, rsync is faster, but if it doesn't copy correctly, it's not worth it)?

Thanks

---

### Post by dcstar on 2011-02-23
> **God Of Atheism said:**
> Hi,

Lately I've tried rsync for backing up my home partition to an external drive, but I've run into some problems with some flac files (there might be other problematic files though, these are the ones I know of).

**The external drive is formatted in ntfs**.

...........

You cannot expect - ever - to properly back up Linux files to non-Linux filesystems.

Linux and Windows filesystems are different, and NTFS does not support all Linux attributes and filenames.

---

### Post by chadhs on 2011-02-28
Does your external drive need to stay NTFS?  What other systems do you need it to attach to?

If you need multi OS access you could just format it as fat32; if not i would recommend formatting it ext3 or ext4 perhaps.

I wrote up a blog post about using rsync to copy a directory but excluding certain files/patterns.  You could take a peak at that and ignore the exclude pieces and pay particular attention to the -n option.  This allows you to do a dry run and "see what rsync would do."  

I'll drop a link to my blog if you care to try that out:
**[http://www.chadstovern.com/copy-all-files-recursively-except-a-pattern-with-rsync](http://www.chadstovern.com/copy-all-files-recursively-except-a-pattern-with-rsync)**

---

