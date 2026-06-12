---
title: "backintime cant remove folder new_snapshot"
date: 2010-08-29
forum: General Help
---

### Post by ndstate on 2010-08-29
Hello,

I am running backintime and I keep getting an error: "backintime cant remove folder new_snapshot" when I am backing up to an external hard drive.

The hard drive is ntfs if that matters.

Anyone have any ideas?

Thanks for your help!

---

### Post by Pollox on 2010-08-29
Idea:
You ran backintime as root before.  You are not running backintime as root now.  Run backintime as root.

---

### Post by ndstate on 2010-08-31
It was ran as root both time.

---

### Post by Pollox on 2010-08-31
Hmm, that was my best guess for the issue.  Could be an issue with backintime.  Could be an issue with permissions on this "new_snapshot" folder.  As root, are you able to remove your old backintime backup (from using "gksu nautilus" or "sudo rm" on the appropriate folder)?  Better yet, have you tested trying to back up in a different folder from your old backup?

---

