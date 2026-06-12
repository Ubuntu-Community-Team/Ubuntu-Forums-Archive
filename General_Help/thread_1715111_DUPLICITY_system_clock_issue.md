---
title: "DUPLICITY: system clock issue"
date: 2011-03-26
forum: General Help
---

### Post by emma_peel on 2011-03-26
Hello forum.

I'm currently facing this bug using DUPLICITY :

```
Local and Remote metadata are synchronized, no sync needed.
Last inc backup left a partial set, restarting.
Last full backup date: Sat Mar 19 14:40:11 2011
Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1239, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1232, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1214, in main
    incremental_backup(sig_chain)
  File "/usr/bin/duplicity", line 474, in incremental_backup
    assert dup_time.curtime != dup_time.prevtime, "time not moving forward at appropriate pace - system clock issues?"
AssertionError: time not moving forward at appropriate pace - system clock issues?

```

The messages above are displayed after a backup. This is slightly irritating, since it happens after a very long backup on a remote box.

I tried a "cleanup", without success.

Does anyone know how to fix this ? Is there some limitation to the use of DUPLICITY ?

---

### Post by uRock on 2011-03-26
Bump for move to General Help.

---

