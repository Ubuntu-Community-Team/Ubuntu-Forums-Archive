---
title: "&quot;deleted inode referenced&quot; ... but that's home!"
date: 2011-04-30
forum: General Help
---

### Post by ccf on 2011-04-30
Things got a little sluggish on one of my machines last night, and it turned out to be DMA uncorrectables.  After prodding and poking the filesystem to see which files are no longer readable, I get this:

```
EXT3-fs error (device sda8): ext3_lookup: deleted inode referenced: 4145153
```

Exploring it with debugfs gives the following:

```
# open -c /dev/sda8 
debugfs: ncheck 4145153
Inode    Pathname
4145153  //chris
```

I would just fsck -y it, but I'm not really up for rendering *my entire home directory* inaccessible.

---

