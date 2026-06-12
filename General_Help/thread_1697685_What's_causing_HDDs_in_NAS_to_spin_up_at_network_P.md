---
title: "What's causing HDDs in NAS to spin up at network PC startup?"
date: 2011-03-01
forum: General Help
---

### Post by bjelakrez on 2011-03-01
I have a NAS box that runs Ubuntu Server and Samba. 4 of the HDDs are in RAID5 (/dev/md1) and I've configured them to spin down after 10 minutes of inactivity. This filesystem is mounted on /share/Media. The other 2 HDDs are NOT configured to spin down.

My other computer runs Ubuntu Desktop. I'm mounting the entire /share folder (that's located on NAS) using this entry in /etc/fstab:```
//192.168.0.1/share /home/ziga/share cifs auto,credentials=/root/.credentials,noserverino 0 0
```

The 4 drives spin down just fine and everything is working smoothly. The only problem is that when I start THIS PC, it causes to spin the drives in NAS box up. The strange thing is that this has been happening for just the past two weeks or so. It used to work fine (i.e. it didn't cause the drives in NAS to spin up at boot).

How can I figure out what's happening? Can I check some of the log files to find out? If so, which ones? Has some update caused it? Recent documents are cleared, they're not the cause. Is there any other "recent" stuff that I should clear?

If I wait for the drives to spin down and then manually unmount and mount /share again, the drives don't spin up. Also, if I boot my Windows PC and mount the /share, it doesn't spin the drives up.

At boot, they spin up just before the Login Screen appears. Does anyone have any idea? I'm lost, don't know what to try next.

---

### Post by prshah on 2011-03-01
> **bjelakrez said:**
> Is there any other "recent" stuff that I should clear?

You might try to check recent locations in the Nautilus file manager (Look under the "Go" menu).

---

### Post by bjelakrez on 2011-03-01
That's cleared as well.

---

