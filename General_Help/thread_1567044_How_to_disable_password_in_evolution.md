---
title: "How to disable password in evolution?"
date: 2010-09-03
forum: General Help
---

### Post by stardustdk on 2010-09-03
Just made a fresh install of Ubuntu 10.04.1.

It is quite annoying that I have to write the password to the POP3 server, every time i check for mail.

(It is not the default keyring).

How to disable the password check for mail?

If it not possible, i have to install another mail program.


Best regards

Stardustdk

---

### Post by gandaran on 2010-09-03
> **stardustdk said:**
> Just made a fresh install of Ubuntu 10.04.1.

It is quite annoying that I have to write the password to the POP3 server, every time i check for mail.

(It is not the default keyring).

How to disable the password check for mail?

If it not possible, i have to install another mail program.


Best regards

Stardustdk
did you mark the remember password box in the mail account setup?

---

### Post by lisati on 2010-09-03
> **gandaran said:**
> did you mark the remember password box in the mail account setup?

I agree that this is probably the best option: I have yet to encounter an email provider that lets you in without a password.

---

### Post by philinux on 2010-09-03
> **stardustdk said:**
> Just made a fresh install of Ubuntu 10.04.1.

It is quite annoying that I have to write the password to the POP3 server, every time i check for mail.

(It is not the default keyring).

How to disable the password check for mail?

If it not possible, i have to install another mail program.


Best regards

Stardustdk

Edit>Prefs>Account> Receiving email options.

---

### Post by stardustdk on 2010-09-03
I have this in order - and i used to work without problems!?

Best regards

Stardustdk

---

### Post by gandaran on 2010-09-03
> **stardustdk said:**
> I have this in order - and i used to work without problems!?

Best regards

Stardustdk
could be keyring problem then 
post here all the file names found in /home/"user"/.gnome2/keyrings

---

### Post by stardustdk on 2010-09-03
default
standardnøglering.keyring

(default.keyring is the second)

Best regards

---

### Post by gandaran on 2010-09-03
> **stardustdk said:**
> default
standardnøglering.keyring

(default.keyring is the second)

Best regards
theres one file missing, the **login.keyring**, try deleting the whole keyrings folder then start evolution, for the keyring password don't enter any, use the unsecured option, enter the pop password then close and open evolution again, maybe this will fix it.
if it doesn't fix it then the only way I know that works is to copy the missing files from another computer keyring setup, I know this works because I already had the same problem and this was the only way I found that could fix the remember password problem, maybe there is a simpler one.

---

