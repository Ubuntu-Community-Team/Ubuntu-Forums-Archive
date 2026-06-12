---
title: "Deja dup error message"
date: 2011-08-07
forum: General Help
---

### Post by bookcrazy on 2011-08-07
So I'm trying to be a good user and back up my hardrive onto my external using deja dup and it his me with this error message: ```
Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1239, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1232, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1133, in main
    sync_archive()
  File "/usr/bin/duplicity", line 910, in sync_archive
    remlist = globals.backend.list()
  File "/usr/lib/python2.6/dist-packages/duplicity/backends/giobackend.py", line 127, in list
    gio.FILE_QUERY_INFO_NOFOLLOW_SYMLINKS)
```

OK, any ideas at all what I'm doing wrong? I used deja dup to back up my last computer without any issues but I seem to be making some kind of mistake this time around. Any help at all would be appreciated.

---

### Post by bookcrazy on 2011-08-07
Man I feel stupid. I went into the settings, adjusted the backup location, and everything worked just fine.

---

