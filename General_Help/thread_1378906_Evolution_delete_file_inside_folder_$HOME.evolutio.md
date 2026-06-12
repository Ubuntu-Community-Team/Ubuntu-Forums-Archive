---
title: "Evolution delete file inside folder $HOME/.evolution/mail/"
date: 2010-01-12
forum: General Help
---

### Post by ellyxc on 2010-01-12
Few mounts ago I installed ubuntu 9.4. I use evolution as my email client, yesterday I logged to my computer and want to check email. I opened the evolution and i 

shocked by the evolution. The evolution display the welcome screen, like first time use. Thank I click forward, in the "Restore from backup" screen I checked "Restore the evolution from backup file" and choose the Inbox file inside $HOME/.evolution/mail/local directory and then click apply. After that evolution display the main screen and I more shocked, I lost all my email. I look at the $HOME/.evolution/mail/local, the evolution deleted all the file and replace with the new zero byte file.

**Is there any way to get my email back? :(**

---

### Post by stevenmansour on 2010-01-13
Evolution just wiped my inbox too, and I don't have a recent backup. I'm not sure what happened - it didn't wipe my account settings since I didn't get the welcome screen and I'm still receiving email - and all folder except for the inbox (including "marked" messages) seem to be intact.

Where can I look to restore my email? After that I'll IMMEDIATELY switch to Thunderbird.

---

### Post by philinux on 2010-01-13
> **ellyxc said:**
> Few mounts ago I installed ubuntu 9.4. I use evolution as my email client, yesterday I logged to my computer and want to check email. I opened the evolution and i 

shocked by the evolution. The evolution display the welcome screen, like first time use. Thank I click forward, in the "Restore from backup" screen I checked "Restore the evolution from backup file" and choose the Inbox file inside $HOME/.evolution/mail/local directory and then click apply. After that evolution display the main screen and I more shocked, I lost all my email. I look at the $HOME/.evolution/mail/local, the evolution deleted all the file and replace with the new zero byte file.

**Is there any way to get my email back? :(**

Restoring evolution uses a file called evolution-backup.tar.gz. This gets created from File>backup settings. If you pointed the restore to anything but this sort of file I'm not sure what evo would do.

---

### Post by ellyxc on 2010-01-18
how I can get my email back? Are there any way?

---

### Post by Cope57 on 2010-01-18
There is no undelete that I know of.

---

### Post by ellyxc on 2010-01-25
So, there is no way to get my old email back? :(

---

