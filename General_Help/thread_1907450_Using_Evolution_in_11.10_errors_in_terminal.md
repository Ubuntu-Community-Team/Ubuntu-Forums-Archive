---
title: "Using Evolution in 11.10 errors in terminal"
date: 2012-01-11
forum: General Help
---

### Post by Handssolow on 2012-01-11
On a desktop my son uses I've just upgraded to 11.10 and decided to remove Thunderbird in Synaptic then open Evolution. Perhaps in the future I'll switch to Thunderbird but I don't want to change just yet.

When I opened Evolution I was shown a box, did I want to migrate? Thinking this was to Evolution I clicked yes but now I'm wondering if this was part of the migration to Thunderbird or have the file names changed which Evolution now uses?

Anyway Evolution seems to be working but if I launch it in the terminal I see these messages and wonder what I need to put right. Do I have to stop this migration process, move or rename some files. On another PC I deleted the mbox local host account based on advice I'd seen in the Forum and I've also removed a local host account on this PC too.

Migrating cached data
Migrating config data
Migrating local user data
  mv /home/handssolowson/.evolution/mail/local/folders.db /home/handssolowson/.local/share/evolution/mail/local/folders.db
  FAILED: Destination file already exists
  rmdir /home/handssolowson/.evolution/mail/local
  FAILED: Directory not empty (contents follows)
          folders.db
  rmdir /home/handssolowson/.evolution/mail
  FAILED: Directory not empty (contents follows)
          local

Edit:I've manually removing Mail/Local/folders.db which seems to have remove the error messages. Seems to have done the trick, fingers crossed.

---

