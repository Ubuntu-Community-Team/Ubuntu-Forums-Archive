---
title: "gtk-recordMyDesktop discard frames"
date: 2011-04-08
forum: General Help
---

### Post by M759 on 2011-04-08
I've spent too many hours at solving this simple issue...
...but I've found the cause, and the fix:D

Description of the problem:

[LIST]
[*]recordMyDesktop "forgets" / "cuts off" the last part of the screen capture
*The last frames are -somehow- skipped*
[/LIST]

 I've mounted my /tmp folder to the RAM using fstab (to relieve my SSD).
/tmp is the default working dir of RecordMyDesktop.

After recording many frames, the /tmp folder's usage is 100%, thus full. Although recordMyDesktop cannot write to the /tmp folder any more, he doesn't show any warning / notice.  To solve this issue, simple change the working dir to a physical disk location. I added the /temp folder for this purpose.

I don't have experienced the following myself, but it seems obvious to me that a full physical disk will also cause this problem. To solve that issue, remove obsolete files, or buy a new Hard disk.

---

