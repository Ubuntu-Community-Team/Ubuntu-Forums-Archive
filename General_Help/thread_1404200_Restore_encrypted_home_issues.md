---
title: "Restore encrypted /home issues"
date: 2010-02-11
forum: General Help
---

### Post by ushills on 2010-02-11
I seem to be having issues with ecryptfs and restoring /home.

I currently have a seperate /home partition and would have created a user with an encrypted /home, I have extracted my passphrase with ```
ecyptfs-unwrap-passphrase .ecryptfs/wrapped_passphrase
``` and stored this separately as *stored_passphrase*.

I have then backed up the users .Private/ folder.

When I delete the user and recreate with encrypted home again and login as user and add the original passphrase with ```
ecrypt-add-passphrase *stored_passphrase*, 
```then logout and restore the backup of .Private/ when I login I cannot access the restored files.

This appears fundamental to me as although I backup my full /home partition currently if I needed to reinstall following a data loss I would not be able to access my encrypted /home folders.

Am I doing something wrong.  Note I do not want to access the files from a live CD, I want to be able to access /home following a reinstallation of the OS.

---

