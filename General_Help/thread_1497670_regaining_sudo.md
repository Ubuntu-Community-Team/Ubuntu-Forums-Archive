---
title: "regaining sudo"
date: 2010-05-30
forum: General Help
---

### Post by notatoad on 2010-05-30
my ubuntu computer recently fried, so i reinstalled.  when i reinstalled, i told ubuntu to import the account from the old install to the new install.  i did not create any other account.  now, when i try to do sudo i get an error saying i am not in the sudoers file.  how can i fix this?

---

### Post by CharlesA on 2010-05-30
Can't you just add the new user to the administrators group?

---

### Post by JustinR on 2010-05-30
> **CharlesA said:**
> Can't you just add the new user to the administrators group?

If he's not in the sudoer's file I don't believe he can change that because he's using his old sudoer's file, which recognizes his new user as an outsider, so he doesn't have administrative priveliges at all.

Use a Live CD to edit the sudoers file, but be careful!

---

### Post by CharlesA on 2010-05-30
Would be simpler to just boot to recovery mode and drop to a root shell. Then use visudo to edit the sudoers file.

*Always use visudo when editing the sudoers file.*

---

