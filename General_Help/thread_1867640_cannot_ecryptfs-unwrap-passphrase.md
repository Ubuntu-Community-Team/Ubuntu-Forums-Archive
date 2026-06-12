---
title: "cannot ecryptfs-unwrap-passphrase"
date: 2011-10-23
forum: General Help
---

### Post by pfwd.tech on 2011-10-23
Hi, 
I've just reset a user password using the link in this post [http://ubuntuforums.org/showthread.php?t=1856995](http://ubuntuforums.org/showthread.php?t=1856995)

I can now access the box but the contents the users  home directory is encrypted in ./private

I've ran:
```
sudo ecryptfs-unwrap-passphrase
```and added the new user login password but it keeps failing.

According to this thread the login passphrase is the users login password
[http://startup-config.com/rescue-data-ecryptfs/](http://startup-config.com/rescue-data-ecryptfs/)

Is there any way to unwrap/rewrap the passphase using the new password that I reset for the user

---

