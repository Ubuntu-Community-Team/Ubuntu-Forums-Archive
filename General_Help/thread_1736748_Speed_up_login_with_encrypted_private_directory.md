---
title: "Speed up login with encrypted private directory"
date: 2011-04-22
forum: General Help
---

### Post by Will Shackleton on 2011-04-22
Hi

I have an encrypted Private directory in ~/Private, set up with ecryptfs-utils. It currently takes several seconds to 'unlock' when I login, and I was wondering if there is any way of making this process concurrent to the rest of the login.
There aren't any files in the folder which are used in the login (keyrings, configs etc), so there shouldn't be any problems with that.
I believe that the folder is decrypted through PAM, so is there an option to background it?

Thanks
Will Shackleton

---

