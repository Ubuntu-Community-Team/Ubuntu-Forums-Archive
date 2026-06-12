---
title: "Strange permissions behaviour with samba/cifs mount"
date: 2011-01-24
forum: General Help
---

### Post by brundles on 2011-01-24
Hi,

I'm hoping someone can help me out with this one as it's confusing me somewhat...

I have a main media PC (running 9.10) which has the music library on it and my laptop (running 10.04) which I tend to use for tagging with the library shared via cifs.

Following the laptops upgrade to 10.04, the cifs mount reverted to root only access - solved easily enough. However then tagging tools (tried Tag & Rename via Wine, and both MusicBrainz and puddletag natively) all report write access issues despite the fact that the same user can create, edit, copy, etc. on that mount point.

At this point, the mount point looks like
```
//192.168.1.4/music on /media/htpcMusic type cifs (rw,mand,noexec,nosuid,nodev)
```
with all files under it having 777 permissions.

Does anyone have any suggestions?

Please! :)

---

