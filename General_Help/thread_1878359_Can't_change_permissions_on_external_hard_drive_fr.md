---
title: "Can't change permissions on external hard drive from 'read only'"
date: 2011-11-09
forum: General Help
---

### Post by aronstandley on 2011-11-09
Hey folks,

I'm trying to clean up an external hard drive, and I keep getting an error that it's read only.

I tried changing the permissions of the file, using "sudo chmod 776 /media/hd-name", but no luck. It came back as 'Read-only file system', with no functional change.
I tried to change the media permissions to 777 too, to see if I could undercut the hard drive, but that hasn't seemed to be working either.

What can I do? I'd like to be able to edit the hard drive's files without needing to go into a sudo browser.

Thanks for your time.

---

### Post by papibe on 2011-11-09
Since it is already mounted read only, you won't be able to change anything. I would advice you to unmount and mount the disk with different options.

Is it an ext3/4 disk or an NTFS?

That is important since the mounting options are different.

Regards.

---

