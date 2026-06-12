---
title: "Why does log in box come up every time I boot?"
date: 2010-11-06
forum: General Help
---

### Post by bigtel on 2010-11-06
I have upgraded to 10.10 and I have a log in box asking for Default Keyring Password every time i boot up. Is there a way to automate this..?

---

### Post by Frogs Hair on 2010-11-06
Aministration Menu > login screen > unlock > set to login automatically as (name).

---

### Post by wilee-nilee on 2010-11-06
> **bigtel said:**
> I have upgraded to 10.10 and I have a log in box asking for Default Keyring Password every time i boot up. Is there a way to automate this..?

Would you just say what the keyring is for, is it your wireless authentication? Give enough information please.

---

### Post by mcduck on 2010-11-06
> **bigtel said:**
> I have upgraded to 10.10 and I have a log in box asking for Default Keyring Password every time i boot up. Is there a way to automate this..?

Yes, it works if you don't use automatic login. The keyring will unlock automatically when you type in your password in Gnome's login screen.

Alternatively you can just set the keyring password to empty one. You'll loose the security that keyring provides, but with automatic login that doesn't really make much difference. To do that go to Applications/Accessories/Passwords and Encryption Keys, right-click the "Default:login"-keyring and select "Change Password". Type in your current password and leave the fields for new one empty.

---

### Post by bigtel on 2010-11-08
> **Frogs Hair said:**
> Aministration Menu > login screen > unlock > set to login automatically as (name).

I have this menu already set to auto log in.

If I leave the system to boot up without putting in the password it does not connect to the internet via the wireless adapter - could this answer your question wilee-nilee?

---

### Post by plucky on 2010-11-08
> **bigtel said:**
> I have this menu already set to auto log in.

If I leave the system to boot up without putting in the password it does not connect to the internet via the wireless adapter - could this answer your question wilee-nilee?

Right click on wireless icon and select **Edit Connections**.
On the window that opens select the wireless tab.Then select your wireless connection and edit.
On the window that opens select "Available to all users".

It should now login without asking for a password and connect to the your wireless.

Good Luck

---

### Post by bigtel on 2010-11-08
Well that seems to have worked..Thanks..!!

Big Tel

---

