---
title: "Deja Dup restore failure"
date: 2011-09-17
forum: General Help
---

### Post by jerguy1928 on 2011-09-17
I have Ubuntu 11.04. I made a backup of my stuff with Deja dup, At the time I had Wubi, but now I have a partition for Ubuntu,(not sure if that is relevant or not), and I am trying to restore it but it is not working. The output is:

```
Failed with an unknown error.

Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1262, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1255, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1209, in main
    restore(col_stats)
  File "/usr/bin/duplicity", line 539, in restore
    restore_get_patched_rop_iter(col_stats)):
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 521, in Write_ROPaths
    for ropath in rop_iter:
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 493, in integrate_patch_iters
    for patch_seq in collated:
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 378, in yield_tuples
    setrorps( overflow, elems )
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 367, in setrorps
    elems[i] = iter_list[i].next()
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 112, in difftar2path_iter
    tarinfo_list = [tar_iter.next()]
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 328, in next
    self.set_tarfile()
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 322, in set_tarfile
    self.current_fp = self.fileobj_iter.next()
  File "/usr/bin/duplicity", line 575, in get_fileobj_iter
    backup_set.volume_name_dict[vol_num],
KeyError: 1
```

---

### Post by MasterMIKE on 2011-10-13
Bump

I just realised I have the same problem. Backed up some files on 11.04. Now that I have 11.10 I wanted to restore them but all I get is this error. Im lucky it was nothing important, but tbh this is a major problem

---

### Post by kentfx on 2011-10-31
It appears that I have literally lost some years of work thanks to DEJA DUP.  

The hard drive on my main computer (a 2 year old HP) failed spectacularly this morning.  There's a 2TB Acer external drive attached to it, which backs up the complete home directory every morning with Deja Dup.  

So I connected the backup drive to my second computer (a Samsung), checked the backup files -- there were 1.1 TB of them -- and clicked Restore.  For about a minute nothing seemed to happen, then Deja Dup reported that there were no backup files to restore.  I checked the backup drive and sure enough, not a single backup file remained on it. 

I've spent the rest of the day trying to recover files, but there's simply no evidence of any files having been on the backup drive.  It's been wiped clean.

I can't tell you how much work has been lost.  The only reason I'm posting this is as a warning -- DEJA DUP IS CAPABLE OF DESTROYING YOUR WORKING LIFE.

Kent Smith
Los Angeles

---

