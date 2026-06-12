---
title: "Deja Dup backup fail"
date: 2012-07-21
forum: General Help
---

### Post by gulmer on 2012-07-21
The first time I set up the backup program it worked w/o any problems, but now when it goes into auto backup or even with manuel backup I get this "Backup Failed" message:
file:///home/gene/Desktop/Screenshot%20from%202012-07-15%2015:08:37.png
Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1403, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1396, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1378, in main
    incremental_backup(sig_chain)
  File "/usr/bin/duplicity", line 563, in incremental_backup
    bytes_written = dummy_backup(tarblock_iter)
  File "/usr/bin/duplicity", line 197, in dummy_backup
    while tarblock_iter.next():
  File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 507, in next
    result = self.process(self.input_iter.next(), size)
  File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 188, in get_delta_iter
    for new_path, sig_path in collated:
  File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 267, in collate2iters
    relem1 = riter1.next()
  File "/usr/lib/python2.7/dist-packages/duplicity/selection.py", line 187, in Iterate
    log.Debug(_("Selecting %s") % subpath.name)
UnicodeDecodeError: 'utf8' codec can't decode byte 0xf1 in position 21: invalid continuation byte
I'm running Ubuntu 12.04 32bit
How can I resolve this error?

---

