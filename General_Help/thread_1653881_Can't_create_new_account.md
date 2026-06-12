---
title: "Can't create new account"
date: 2010-12-27
forum: General Help
---

### Post by nPn_ on 2010-12-27
I want to create a new account (just so that I can change the uid of my current account to match my afs id).
I have started out using the gui system->admin->users and group
Everything seems to work but I could not login.  I finally tracked ti down to the account being marked disabled.  I unchecked the box in the disable account box (in the advanced settings) and apply, etc. but when i come back in it is re-checked

I tried in the command line
sudo passwd -S account_name
and i get back
account_name P 12/27/2010 1 90 7 -1
i think the -1 means it is disabled
I run
sudo usermod -p new_pass_word account_name
sudo passwd -u account_name
which comes back without any errors but then
sudo passwd -S account_name 
comes back with the same info
and if i just try
su account_name 
i get Authentication failure back


any ideas?

nPn

---

### Post by karthick87 on 2010-12-27
[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

---

### Post by TeoBigusGeekus on 2010-12-27
Delete this account
```
sudo userdel -r account_name
```
and try adding a new one from terminal
```
sudo useradd -m -G [groups you want the account to be a part of] -s /bin/bash account_name
```
After you create it, create a password for it as well
```
sudo passwd account_name
```
Post back with the results.

---

### Post by nPn_ on 2010-12-27
> **TeoBigusGeekus said:**
> Delete this account
```
sudo userdel -r account_name
```and try adding a new one from terminal
```
sudo useradd -m -G [groups you want the account to be a part of] -s /bin/bash account_name
```After you create it, create a password for it as well
```
sudo passwd account_name
```Post back with the results.

Thanks!!  that helped.  Turns out the password I was using was too weak.
When I used sudo passwd -p  it never complained but when I let it prompt me it did

Thanks - nPn

---

