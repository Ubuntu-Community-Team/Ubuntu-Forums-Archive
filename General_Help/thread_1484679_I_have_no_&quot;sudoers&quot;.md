---
title: "I have no &quot;sudoers&quot;"
date: 2010-05-16
forum: General Help
---

### Post by GroogFish on 2010-05-16
I have only one user and it is not a sudoer. Since I can't use the sudo command I can't make him a sudoer. What should I do?

---

### Post by inso_741 on 2010-05-16
have you tried loging in as root?
and why cant you use sudo?

---

### Post by melrokz on 2010-05-16
Your Ubuntu installation seems to be corrupt :-(

---

### Post by Ozymandias_117 on 2010-05-16
Hold shift at boot up and select recovery mode, that will allow you to login to root without a password to fix it.

Note: In a regular Ubuntu installation, the admin group is assigned sudo privileges and your account will be included in the admin group.

---

### Post by melrokz on 2010-05-16
Yes, I agree that using the 'recovery mode' option will help you logon as root and fix your system. Just type:

visudo

will show you the sudoers file, if it is there.

---

