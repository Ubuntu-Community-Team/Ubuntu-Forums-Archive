---
title: "cd mounted across all sessions so cannot eject"
date: 2010-01-11
forum: General Help
---

### Post by Highway on 2010-01-11
Hi,
I am using Ubuntu 9.10.
We have a family laptop shared between multiple family members.  There are usually at least 2 active sessions always logged in.  

When i insert a cd or dvd it mounts fine as expected in my session.  When i'm finished with it, and try and umount it, I am told that:

Error unmounting: umount exited with exit code 1: helper failed with:
umount: only avril can unmount /dev/scd0 from /media/cdrom0

This is because it was also mounted in Avrils session as she was logged in at the time.

I either have to Switch User to her session and umount it there, or do it as root using sudo in my session.  

Is this behaviour configurable?  Can the cd/dvd be only mounted in the session that actually inserts it, and not attached to any other sessions that may be logged in at the time.

Thanks,
Highway.

---

