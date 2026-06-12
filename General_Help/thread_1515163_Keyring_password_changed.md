---
title: "Keyring password changed????"
date: 2010-06-21
forum: General Help
---

### Post by learning_ on 2010-06-21
I recently changed my password, restarted my comp several times since then, and then today (roughly 23:30 est) i received an error message stating that my keyring password had changed since i last needed to use it. i dont know why it changed only the login pass and not the 'keyring' pass too. i cannot figure out how to actually change the keyring pass... this poses no actual problem, merely an inconvenience... can anybody tell me what i need to do to change this please?

---

### Post by maxdakota on 2010-06-22
I think you should try to re change it. Follow the lines,
Programs-> Accessories-> Keyrings
Password tab
Rightclick and select change password

---

### Post by timzak on 2010-06-24
> **maxdakota said:**
> I think you should try to re change it. Follow the lines,
Programs-> Accessories-> Keyrings
Password tab
Rightclick and select change password

Thanks, I just had the same issue.  IMO this is not a good system.  When you change your system password, it should change the keyring password at the same time.  Also, right-clicking to change the password is not intuitive either.  This is the only way in the GUI to change the keyring password for login, no menu settings appear to do this.  Anyhow, not complaining at you, just commenting.  I appreciate your solution.

---

### Post by learning_ on 2010-07-03
well I tried that, but nothing changed. I still get the password prompt. My very first password is the one it keeps asking for to unlock the keyring. Lets say [ Pass = example_1 ] and I changed it to [ Pass = 2example ]. Now every time I login, it asks me for my new password [2example] then it says 

"Enter password to unlock your login keyring
The password you use to login to your computer no longer matches that of your login keyring"

So I enter my original password [example_1]. When I change the login keyring password through Applications>Accessories>Login And Encryption Keys, I recieve the same pop-up window when I login to my computer asking for the same password. How do I change the keyring password to the same password as my login?

---

### Post by Cason on 2010-07-04
> **learning_ said:**
> well I tried that, but nothing changed. I still get the password prompt. My very first password is the one it keeps asking for to unlock the keyring. Lets say [ Pass = example_1 ] and I changed it to [ Pass = 2example ]. Now every time I login, it asks me for my new password [2example] then it says 

"Enter password to unlock your login keyring
The password you use to login to your computer no longer matches that of your login keyring"

So I enter my original password [example_1]. When I change the login keyring password through Applications>Accessories>Login And Encryption Keys, I recieve the same pop-up window when I login to my computer asking for the same password. How do I change the keyring password to the same password as my login?

I was having the same trouble, but I noticed something: if you're trying to change the password, and your new password is the exact same as the old except with some new characters added, it refuses to change the password, except it won't *tell* you that. I don't know about you, but I was trying to use the same password that I had before except with some extra characters at the end. ;)

But even if that isn't your problem, this should work: change both your login password and your keyring password to something temporary (but the same temporary password for both). Then reboot and then change both again, this time with the new desired password. As long as you change both to the same thing, it should quit asking you to enter it every time you boot up. That's how it worked for me anyway. :D

---

### Post by learning_ on 2010-07-07
> **Cason said:**
> I was having the same trouble, but I noticed something: if you're trying to change the password, and your new password is the exact same as the old except with some new characters added, it refuses to change the password, except it won't *tell* you that. I don't know about you, but I was trying to use the same password that I had before except with some extra characters at the end. ;)

But even if that isn't your problem, this should work: change both your login password and your keyring password to something temporary (but the same temporary password for both). Then reboot and then change both again, this time with the new desired password. As long as you change both to the same thing, it should quit asking you to enter it every time you boot up. That's how it worked for me anyway. :D


Thanks, That worked perfectly actually. I've been trying to get that for months. It happened before but somehow it just stopped... then came back. Thanks again :D

---

