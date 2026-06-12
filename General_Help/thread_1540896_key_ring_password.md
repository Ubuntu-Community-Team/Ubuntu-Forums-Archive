---
title: "key ring password"
date: 2010-07-28
forum: General Help
---

### Post by bhmildy on 2010-07-28
Hi Everyone.
Back when 10.04 was new, I installed Ubuntu and logged on to my wifi router.  Ubuntu asked me to make a key ring password.  Not knowing what a key ring was, I decided not to have one.  Now that I know it's a good idea, how do I go back and get that key ring going, with a password, and all encrypted, like I should have?
Thanks for your help!

---

### Post by cj13579 on 2010-07-28
Under Applications > Accessories > Passwords and Encrypted Keys

You will probably have 2 entries: login and default. Right click on default and select change password.

---

### Post by mcduck on 2010-07-28
Just go to Applications/Accessories/Passwords and Encryption Keys. Then, on the Passwords-tab, right-click the "Passwords:login"-keyring and select "Change Password". Now you'll be able to set the password for your keyring.

If you set the keyring password to the same as your login password, your keys will be stored in encrypted format but the keyring will be unlocked automatically for you when you log in (but this only works if you actually use the login screen, not automatic login).

If the password is different, or you use automatic login, you will be prompted for keyring password when any application tries to access the keyring. Usually this happens immediately when your desktop loads, when the Network Manager needs the password for a wireless network...

---

### Post by cj13579 on 2010-07-28
> **mcduck said:**
> . Usually this happens immediately when your desktop loads, when the Network Manager needs the password for a wireless network...

Yep, this is really annoying! I had pam working in 9.04 but it has stop since recent upgrade. Do you know if there is any way to get this working again?

P.s. This isn't a thread steal or anything...

---

### Post by mcduck on 2010-07-28
> **cj13579 said:**
> Yep, this is really annoying! I had pam working in 9.04 but it has stop since recent upgrade. Do you know if there is any way to get this working again?

P.s. This isn't a thread steal or anything...

Annoying? If you are using a different passwords for login and keyring, or automatic login, that's the *correct* behavior... :D

If you *do* use the same password for both login & keyring, and *aren't* using automatic login, then this of course shouldn't happen. I can't really say what might cause it to behave like that, but the first thing I'd try would be creating a new user account to see if the problem exists only for one user or all of them. Of course you could also just *unset* the keyring password, especially if you aren't storing any top-secret stuff there.

---

### Post by cj13579 on 2010-07-28
I am using automatic login so maybe I will turn that off for a while and see how that goes.

---

### Post by bhmildy on 2010-07-31
Thanks folks.  I can't tell if anything is different after following these instructions, but it looks good to me and I appreciate the help.  Kind regards.

---

