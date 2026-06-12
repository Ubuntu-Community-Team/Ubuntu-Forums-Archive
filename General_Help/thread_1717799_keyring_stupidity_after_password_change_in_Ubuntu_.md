---
title: "keyring stupidity after password change in Ubuntu 10.04"
date: 2011-03-30
forum: General Help
---

### Post by Schuby007 on 2011-03-30
Hi,

A standard user on an Ubuntu 10.04 desktop changed their login password but Ubuntu keyring keeps asking for their old password when they try to access Evolution email. How do I fix this?

Thank you,
Schuby

---

### Post by matt_symes on 2011-03-30
Hi

Try

Applications->Accessories->Passwords and encryption keys.

Right click on his passwords entry and select change password. Change to his new password.

If that does not fix it try deleting that evolution key under passwords.

Hopefully one of them will work.

Kind regards

---

### Post by Schuby007 on 2011-03-30
> **matt_symes said:**
> Hi

Try

Applications->Accessories->Passwords and encryption keys.

Right click on his passwords entry and select change password. Change to his new password.

If that does not fix it try deleting that evolution key under passwords.

Hopefully one of them will work.

Kind regards

Hi! Thank you for your quick reply! I will try this as soon as I can. It sounds like a very simple solution, however I cannot understand why it's necessary... What desktop user is gonna know to update their keyring file after changing their password?? Am I dreaming in techni-color to expect the system to do it automatically??

I build computers as a side job and I've been trying to promote Ubuntu to my clients (Windows users) and it's very hard to do when a simple password change causes the email to stop working...

---

### Post by Schuby007 on 2011-03-30
Hey,

I tried the first recommendation ("right click passwords entry -> change password") that "fixed it". I still don't see why after they have logged into the computer, they have to enter their password again to access the email. It would make sense to me that when they sign in, the keyring gets unlocked...

Thanks again for the help.

---

### Post by matt_symes on 2011-03-30
Hi

The reason why is it allows extra security if the keyring password is different from the log in password. Hacking your account is one thing, getting your secrets (bank passwords) is another.

Glad it's fixed though :D

Remember, Linux is not windows ;) (No offense to windows intended)

Kind regards

---

