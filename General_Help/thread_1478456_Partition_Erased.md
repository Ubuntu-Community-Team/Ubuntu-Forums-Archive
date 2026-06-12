---
title: "Partition Erased?"
date: 2010-05-09
forum: General Help
---

### Post by spvo on 2010-05-09
I just did a fresh install of 9.10 on my desktop.  I picked the manual partition, and set up all my hard drives.

I have a 1.5T hard drive that I use strictly for media and told the installer to mount it at a particular point.  Mistakenly I also told it to use the hard drive as an ext4 partition when in fact it was an ext3 partition.  The format checkbox was NOT checked.

Ubuntu installed perfectly, but despite the format option being off, no files show up on the mounted hard drive.  Were the files erased?  Is there any possible way to recover them?

Thanks

---

### Post by flyingmonkey35 on 2010-05-09
Ouch sorry to hear that,
 
That depends, you may be able to recover, using some recovry tools,
 
this will take time, 
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by bobnutfield on 2010-05-09
I hope you are able to recover your files.  This is a "gotcha" that sneaks up on you.  I lost all of the files in my home partition when upgrading, even though I also instructed the installer NOT to format the ext4 file system.  There should definitely be a warning when changing from ext3 to ext4 on a separate /home partition.

---

### Post by spvo on 2010-05-09
Thanks for the quick replies.  Yeah, I agree, a warning would have been really nice.

I've used photorec before to recover files from my camera, and it looks like it would work pretty well for media files as well.  Has anyone had better luck with other programs?

Bobnutfield, were you able to recover most of your files?  If so, what program did you use?

---

### Post by bobnutfield on 2010-05-11
> Bobnutfield, were you able to recover most of your files? If so, what program did you use?

Fortunately, I had complete backups of all my files, so recovery was not necessasry.  Still, it would have been nice to have been warned that if I changed the filesystem on the partition, it would be formatted.

---

