---
title: "NFS,AutoFS Issues"
date: 2011-01-12
forum: General Help
---

### Post by jngrim on 2011-01-12
I have a NFS share mounted remotely to another meerkat box wirelessly. I noticed that when I mounted the share via fstab, the files/folder did not always display in Nautilus.  I decided to try using autofs to mount the share, but I get the same problem.  It take about 5 minutes before I can start navigating through the remote share directories.  Is this a problem with NFS?  It's frustrating because when I use the remote share to be my media server, not all the files or folders are available

I did test the directors by 'cd'ing using the CL and I can navigate down various levels and appears to be more stable. Can anyone explain this?

Also on another note, I did notice a significant bandwidth impact when I moved from fstab to AutoFS for the media share....I went from 2MiB/s to 1.4MiB/s. Does anyone have any ideas why or what I can do to fix it?

thanks

---

