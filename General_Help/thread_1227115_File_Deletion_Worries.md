---
title: "File Deletion Worries"
date: 2009-07-30
forum: General Help
---

### Post by Lunarizing on 2009-07-30
Running U 9.04 as a file server/vault.  It's wide open, has to be that way for Autodesk C3d to operate properly.  I make daily backups and monthly back ups.  The concern is that someone could delete files that go un-noticed for an extended period of time.  Is there a way to log deletion activity?  Maybe with size of file parameters?  Or some way to have all deletion activity (other than Cad) require a password or a password with restrictions?  I realize I'm all over the board here with what I'm asking for, but I think my main concern is apparent.  Any help will be appreciated greatly.

---

### Post by asmoore82 on 2009-07-30
rsync will maintain the files in a backup location but will not delete
missing files from the backup location unless you explicitly tell it to.

then the concern becomes someone maliciously *truncating* files instead of just deleting them ...

As long as it is "wide open," some combination of rsync'ing and archiving is probably your best bet.

---

