---
title: "rm -rf /*"
date: 2010-12-30
forum: General Help
---

### Post by Vorfin on 2010-12-30
Ok, well I did something stupid, I put "rm -rf /*" into the Terminal to see what would happen. I expected there to be some kind of "Are You Sure?" Message like you get with Windows if you put "del C:" in there, but I guess not. :lolflag:

Anyway, I saw a few "access denied" messages fly past, and closed the Terminal A.S.A.P. Sadly however some things got deleted, like the Shortcuts in my Places Menu (My "Documents" and "Pictures" Folders are ok, THANK GOD!) While some other things like my Downloaded Emails in Evolution, and Default Browser Settings have been removed.

None of this is a big deal really, however I am rather worried if I shutdown, I wont come back =S So does Ubuntu have some kind of Restore/Repair Disk/Tool I can run to either fix the boot files(if damaged/deleted) or restore the system to before I did this?

Thanks :KS

---

### Post by matt_symes on 2010-12-30
Hi

That was very silly indeed.

Unless you have made backups you could be in serious problems. I expect alot more got deleted than just files in you home directory. Did you run it as sudo? If you did... Now where's that Ubuntu install disc again?

Kind regards

---

### Post by Vorfin on 2010-12-30
> **matt_symes said:**
> Hi

That was very silly indeed.

Unless you have made backups you could be in serious problems.

Kind regards

I have backups of all my personal files, Music, Documents, Applications, Ect, however I don't have Backups of the System Files. I know a fresh install would just fix it all, and probably be quicker. But hey, I wondered if Ubuntu had any tools in anticipation of "silly" "mistakes" like this.

EDIT: No, I didn't use sudo, I'm not some kind of idiot :3 hehe

---

### Post by TeoBigusGeekus on 2010-12-30
Write somewhere the commands from my post in [here]("http://ubuntuforums.org/showthread.php?t=1653881"), boot into recovery mode and create another account. Boot with this account and you should be fine; you will have however lost all your settings.
Since you didn't use sudo, nothing of importance to the system is lost.
You can however do it again using sudo for our amusement. :lolflag:

---

### Post by foxmulder881 on 2010-12-30
I'm sorry to hear of your troubles and loss. But at the same time, it's also quite funny because at some point in our beginnings in the world of GNU/Unix, we've all done it, "just to see what happens".

But to answer your question, whatever you chopped with that command is gone with no chance of revival.

---

### Post by Vorfin on 2010-12-30
> **TeoBigusGeekus said:**
> Write somewhere the commands from my post in [here]("http://ubuntuforums.org/showthread.php?t=1653881"), boot into recovery mode and create another account. Boot with this account and you should be fine; you will have however lost all your settings.
Since you didn't use sudo, nothing of importance to the system is lost.
You can however do it again using sudo for our amusement. :lolflag:

Thanks, however on second thoughts I am just going to do a fresh install. Much quicker. However after I finish checking all my backups I might just run it using sudo for the hell of it.

---

### Post by matt_symes on 2010-12-30
Hi

That account is trashed. Glad you had backups. Follow Teo's advice.

EDIT: Just seen your final post. Do it in a VM.

Kind regards

---

### Post by daqron on 2010-12-30
> **Vorfin said:**
> However after I finish checking all my backups I might just run it using sudo for the hell of it.
I am curious at what point the system is unable to continue deleting files as a result of critical system files having been deleted. I might have to try this too (in a VM, as matt_symes suggests).

---

### Post by TeoBigusGeekus on 2010-12-30
Brilliant idea! It reminds me of [this]("http://ubuntuforums.org/showthread.php?t=72598").

---

### Post by srs5694 on 2010-12-30
If you did it as an ordinary user (without using sudo), the system will still boot fine. It's possible you'll have problems logging in because of missing account files, but the system will boot. If you can't log in, you should be able to recover your account (or create a new one) using various recovery methods. I'd suggest using this as a way to learn about such techniques rather than go back and re-install everything from scratch. (I'm afraid I don't have URLs to Web pages that describe such recovery techniques, but I'm sure a Google search will turn something up.)

---

### Post by ibuclaw on 2010-12-30
> **srs5694 said:**
> If you did it as an ordinary user (without using sudo), the system will still boot fine. It's possible you'll have problems logging in because of missing account files, but the system will boot.

Which get replaced with the default settings if missing. Logging in will not be an issue. Just loss of personal data.

---

### Post by theozzlives on 2010-12-30
You do realize that any drives and/or partitions that are mounted will be wiped clean. That command is a sever no no!

---

