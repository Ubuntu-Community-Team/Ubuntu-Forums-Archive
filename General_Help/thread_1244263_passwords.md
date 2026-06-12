---
title: "passwords"
date: 2009-08-19
forum: General Help
---

### Post by trampintransit2 on 2009-08-19
whnever i open Evolution for the first time it asks me for my password, can i disable this?

---

### Post by mcduck on 2009-08-19
> **trampintransit2 said:**
> whnever i open Evolution for the first time it asks me for my password, can i disable this?

Are you using automatic login? As in not typing your password to log into the desktop..

Evolution, like many other programs, stores passwords into Gnome's keyring. If you use normal login the keyring is unlocked automatically. But with passwordless login that's not possible, so you need to unlock the keyring yourself.

If you want to keep on using the automatic login, your only option is to remove keyring password. This means that all your network keys, passwords etc. are stored unencrypted, but since you are using automatic login that's probably not an issue for you.. ;)

To remove keyring password open Applications/Accesories/Passwords and Encryption Keys. The  go to Passwords-tab, right-click the "Passwords:login"-keyring, select "Change Password", type your old password and leave the fields for new one empty.

---

