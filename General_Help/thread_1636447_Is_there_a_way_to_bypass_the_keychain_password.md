---
title: "Is there a way to bypass the keychain password?"
date: 2010-12-03
forum: General Help
---

### Post by the lemming on 2010-12-03
I realise that passwords are a good thing but I'm getting fed up having to enter a password just to get my wireless network to work every time I switch on Ubuntu or when I log out and back in again.

Seeing as there is nobody in the house that I want to keep away from the computer, is there a way to automatically sign-in to my wireless network without having that annoying key-chain popping up every time?

Cheers

---

### Post by mendhak on 2010-12-03
Hi lemming, have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=920250](http://ubuntuforums.org/showthread.php?t=920250)

---

### Post by mcduck on 2010-12-03
If you use normal login (instead of automatic login) and you keychain password is same as your login password, the keychain will unlock automatically.

If you want to use automatic login your only option is to remove the keychain password. It's less secure, but that makes really no difference on a system that uses automatic login, so that shouldn't be any problem.

To remove the keychain password go to System/Preferences/Passwords and Encryption Keys, right-click on the "default:login"-keychain and select "Change Password". Type in your current password and leave the fields for new one empty.

(of course if it's just the network connection that uses the keychain on your system, you can simply go to the connection's preferences and mark the "available to all users" checkbox. )

---

### Post by the lemming on 2010-12-03
Thanks for the advice.

How would I remove automatic login please?

That way I will be able to keep the key-chain but not have to type in a password?

Cheers

---

### Post by Spyderkid on 2010-12-03
to remove auto-matic login go to system> administration> then Users and groups, go onto your person click on advanced settings then click on the bit where it says:....

Password: not asked on login

click on the not asked on login re-entre your password and uncheck the asked on login box and click ok

---

### Post by mcduck on 2010-12-03
> **the lemming said:**
> Thanks for the advice.

How would I remove automatic login please?

That way I will be able to keep the key-chain but not have to type in a password?

Cheers

nope, you'll keep the keychain but will need to type in your password at the login screen. ;)

If you just want everything to work without typing your password *at any point* then removing the keychain password is the only way.

(and it doesn't remove the keychain, it still works just fine, it just stores your keys unencrypted. Which makes no difference since without a login password anybody with access to the computer would get your passwords, and everything else, anyway)

---

