---
title: "xfs inode flush bugs -- threat or menace?"
date: 2010-07-01
forum: General Help
---

### Post by nutznboltz on 2010-07-01
I was rather intrigued by the large number of xfs bug fixes in the recent kernel update for Lucid.

```
aptitude changelog linux-image-2.6.32-23-server | grep -c xfs:
20
```

20!

Poking around reveals that one Dave Chinner, Principal Engineer -- SGI Australian Software Group, submitted a series of patches to deal with preventing the flushing of stale inodes.

I'm trying to figure out just how relevant those patches are to the stability of XFS, especially to pre-Lucid Ubuntu systems: are they in danger of data loss?

Some quick search results thrown together in an effort to asses this issue:

[http://lkml.org/lkml/2010/4/26/118](http://lkml.org/lkml/2010/4/26/118)
> Dave Chinner (9):
      xfs: Don't flush stale inodes
      xfs: Ensure we force all busy extents in range to disk
      xfs: reclaim inodes under a write lock
      xfs: Avoid inodes in reclaim when flushing from inode cache
      xfs: reclaim all inodes by background tree walks
      xfs: fix stale inode flush avoidance
      xfs: xfs_swap_extents needs to handle dynamic fork offsets
      xfs: don't hold onto reserved blocks on remount, ro
      xfs: Non-blocking inode locking in IO completion



[http://archives.free.net.ph/message/20100422.190747.90baa462.el.html](http://archives.free.net.ph/message/20100422.190747.90baa462.el.html)
> Because inodes remain in cache much longer than inode buffers do under memory pressure, we can get the situation where we have stale, dirty inodes being reclaimed but the backing storage has been freed. Hence we should never, ever flush XFS_ISTALE inodes to disk as there is no guarantee that the backing buffer is in cache and still marked stale when the flush occurs. 

[http://kerneltrap.org/mailarchive/git-commits-head/2010/6/5/41549](http://kerneltrap.org/mailarchive/git-commits-head/2010/6/5/41549)
> Unfortunately, xfs_ifree_cluster() has some bugs that lead to inodes not being marked with XFS_ISTALE. This shows up when xfs_iflush() is called on these inodes either during inode reclaim or tail pushing on the AIL.  The buffer is read back, but no longer contains inodes and so triggers assert failures and shutdowns.  This was reproducable [sic] with at run.dbench10 invocation from xfstests.

Reproducible assert failures and shutdowns?

---

### Post by nutznboltz on 2010-07-02
Dave Chinner said that the xfs stale inode cache flush bugs have only been reported by people with systems that have *very* high inode turn-over rates.

---

