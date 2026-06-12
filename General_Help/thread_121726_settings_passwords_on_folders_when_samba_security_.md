---
title: "settings passwords on folders when samba security is set to shared."
date: 2006-01-25
forum: General Help
---

### Post by bb002 on 2006-01-25
I'd like to know how to set a password on a shared folder in samba when security=share in smb.conf.

I'm trying to set samba up to act like a windows 98 machine.

so when someone tries to access the samba share "\\BigBadBox\Freddy" they get prompted for a password.
But if someone tries to access the samba share "\\BigBadBox\ThePub" they are let in.

Anyone know how to do this? I've googled everywhere and can only find ones that are for when security is set to user.

---

### Post by patrick295767 on 2006-06-27
[QUOTE=bb002]I'd like to know how to set a password on a shared folder in samba when security=share in smb.conf.

I'm trying to set samba up to act like a windows 98 machine.

so when someone tries to access the samba share "\\BigBadBox\Freddy" they get prompted for a password.
But if someone tries to access the samba share "\\BigBadBox\ThePub" they are let in.

Anyone know how to do this? I've googled everywhere and can only find ones that are for when security is set to user.[/QUOTE]
  
I have same problem with WINDOWS 98 SE
i even tried no passwd . It's not working so
it's meaning sthg . ... there is a big problem 

which is coming from WINDOWS 98 i guess .... since  linux can mount the smbfs share with the right passwd. 

:-k :-k :-k :-k :-k
  
I am updating service pack of W98 se ... 
i guess it'll work

---

