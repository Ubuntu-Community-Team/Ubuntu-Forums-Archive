---
title: "Duplicity Restore Error"
date: 2012-08-22
forum: General Help
---

### Post by dcheifer on 2012-08-22
I'm in a bad situation -- the drive on which I store all of my documents, photos, music, videos, etc. has stopped working.  I had been using Deja Dup for automated backups, and there appears to be a full backup from a few days before the crash.  When I attempt to restore with Deja Dup to a new hard drive, Deja Dup appears to start the restore process, but the progress bar remains empty, even after several hours and nothing shows up on the destination drive.  

Following the procedure outlined in Deja Dup's help document, I've tried to restore via command line, and when I do I get a lengthy string of errors that look like thes:

Error '[Errno 1] Operation not permitted: '/media/Shared/Restored/home/dcheifer/.gconf/apps/nautilus/desktop-metadata/SHARED@46@volume/%gconf.xml'' processing home/dcheifer/.gconf/apps/nautilus/desktop-metadata/SHARED@46@volume/%gconf.xml
Error '[Errno 1] Operation not permitted: '/media/Shared/Restored/home/dcheifer/.gconf/apps/nautilus/desktop-metadata/SHARED@46@volume'' processing .


Followed by the following once at the end of the list:

Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1359, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1342, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1276, in main
    restore(col_stats)
  File "/usr/bin/duplicity", line 591, in restore
    restore_get_patched_rop_iter(col_stats)):
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 523, in Write_ROPaths
    ITR( ropath.index, ropath )
  File "/usr/lib/python2.7/dist-packages/duplicity/lazy.py", line 338, in __call__
    self.process_w_branch(index, branch, args)
  File "/usr/lib/python2.7/dist-packages/duplicity/lazy.py", line 293, in process_w_branch
    branch.start_process, args)
  File "/usr/lib/python2.7/dist-packages/duplicity/robust.py", line 37, in check_common_error
    return function(*args)
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 555, in start_process
    assert index == (), index
AssertionError: ('home', 'dcheifer', '.gconf', 'apps', 'nautilus', 'desktop-metadata', 'Shared@46@volume')

Any ideas on what the issue might be here?

---

### Post by mzaam on 2012-08-22
maybe you should run dejadup as root,

or try install testdisk to recover your disk.

---

### Post by enigmaingr on 2012-09-04
> **dcheifer said:**
> I'm in a bad situation -- the drive on which I store all of my documents, photos, music, videos, etc. has stopped working.  I had been using Deja Dup for automated backups, and there appears to be a full backup from a few days before the crash.  When I attempt to restore with Deja Dup to a new hard drive, Deja Dup appears to start the restore process, but the progress bar remains empty, even after several hours and nothing shows up on the destination drive.  

Following the procedure outlined in Deja Dup's help document, I've tried to restore via command line, and when I do I get a lengthy string of errors that look like thes:

Error '[Errno 1] Operation not permitted: '/media/Shared/Restored/home/dcheifer/.gconf/apps/nautilus/desktop-metadata/SHARED@46@volume/%gconf.xml'' processing home/dcheifer/.gconf/apps/nautilus/desktop-metadata/SHARED@46@volume/%gconf.xml
Error '[Errno 1] Operation not permitted: '/media/Shared/Restored/home/dcheifer/.gconf/apps/nautilus/desktop-metadata/SHARED@46@volume'' processing .


Followed by the following once at the end of the list:

Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1359, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1342, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1276, in main
    restore(col_stats)
  File "/usr/bin/duplicity", line 591, in restore
    restore_get_patched_rop_iter(col_stats)):
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 523, in Write_ROPaths
    ITR( ropath.index, ropath )
  File "/usr/lib/python2.7/dist-packages/duplicity/lazy.py", line 338, in __call__
    self.process_w_branch(index, branch, args)
  File "/usr/lib/python2.7/dist-packages/duplicity/lazy.py", line 293, in process_w_branch
    branch.start_process, args)
  File "/usr/lib/python2.7/dist-packages/duplicity/robust.py", line 37, in check_common_error
    return function(*args)
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 555, in start_process
    assert index == (), index
AssertionError: ('home', 'dcheifer', '.gconf', 'apps', 'nautilus', 'desktop-metadata', 'Shared@46@volume')

Any ideas on what the issue might be here?
I have an identical issue. It seems that there is something wrong with Deja Dup and Duplicity in 12.04. I can't backup or restore after a clean install to 12.04.

---

