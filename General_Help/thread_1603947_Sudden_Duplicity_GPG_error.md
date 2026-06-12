---
title: "Sudden Duplicity GPG error"
date: 2010-10-23
forum: General Help
---

### Post by rbroom on 2010-10-23
I've been using Duplicity for ages and this morning it suddenly produces the following error:
```
~$ duplicity --encrypt-key="FFFFFFFF" /home/user scp://user@backupserver//home/Drive1/UserDir
Local and Remote metadata are synchronized, no sync needed.
Last full backup date: Fri Oct 22 17:14:53 2010
GPGError: GPG Failed, see log below:
===== Begin GnuPG log =====
gpg: decrypt_message failed: eof
===== End GnuPG log =====
```

I can't figure out what happened.  Yesterday I did a successful full backup (as I do each week).  This command was to add the usual incremental.  I've not changed the scripts, source, destination or GPG keys.  I turned up verbosity to see what it was doing, but an obvious error didn't leap out.  A search of the forums and 'net in general didn't turn up anything helpful.  

Does anyone have an idea of what's going on here?

---

### Post by rbroom on 2010-10-25
I was unable to recover from the error, but I did resolve it by deleting the remote backup sets (all of them) and doing a new full backup.  Now I'm able to perform incrementals and get status again.

---

### Post by dgchurchill on 2011-11-02
For people coming from Google with the same problem:

When this occurred for me I noticed there were zero-sized .gpg files in the backup destination.  Removing these files appears to have solved the problem (I haven't yet tried a restore, but backing up no longer shows the GPG error).

---

