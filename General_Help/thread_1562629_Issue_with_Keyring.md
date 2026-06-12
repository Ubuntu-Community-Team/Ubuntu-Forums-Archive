---
title: "Issue with Keyring"
date: 2010-08-27
forum: General Help
---

### Post by Horrendus01 on 2010-08-27
Okay here is the situation.  I just re-sized my windows partition on my laptop and installed 10.04.1.  Brand new clean install.  I set up my user account, gave it a password, and everything was fine until I tried to connect to my wireless.  I typed in the security key for my wireless, and it asked for a password to unlock the default keyring.  The problem is, I never set a password for the "default" keyring.  I never changed my user password.  I didn't auto-login, I entered my password.  This was the first boot up of the machine after installing 10.04.1.  I can't use Empathy, because the keyring cannot be unlocked.  If I "cancel" it gives me an error saying the account details are wrong, but I log into my facebook, aim, and msn every day, so I know the passwords are correct.

I have read about other issues with the keyring, and with the auto-login bug that is associated with it.  I have also read up on the bug that occurs with that as well.  I couldn't find anything about my specific situation, so I hope this isn't a re-post of an issue that has already dealt with, but I did look it up.  

Hopefully someone would be kind enough to help me fix this issue, if they know how.  

Thanks in advance!

Rob

EDIT:

If it helps, the laptop I am running is a HP Pavilion dv7-3065dx, and I have Ubuntu Desktop 10.04.1 x86 installed.  Clean install and the only thing I have done was log in, connect to network, and try to set up Empathy.  Both Empathy, and connecting to network, gave me the issues with the keyring.  It appears that there is already a password for the default keyring, it is not blank, and my user login password does not work for it.  I'm at a loss...

---

### Post by Horrendus01 on 2010-08-28
Nevermind I fixed the issue.  I just rm the keyring and made a new one.

---

