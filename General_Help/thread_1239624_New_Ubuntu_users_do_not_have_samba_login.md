---
title: "New Ubuntu users do not have samba login"
date: 2009-08-13
forum: General Help
---

### Post by mpsrig on 2009-08-13
I just created a second ubuntu user.  Now, on my other computer i should be able to log in over samba with that user name and password, right?
Except that instead it just bounces back to saying "guest" rather that "username".

---

### Post by rbc on 2009-08-13
I think you have to create a samba username and password on the computer you want to connect to:
sudo smbpasswd -L -a *username*
You should then be prompted, twice, for the samba password

---

### Post by mpsrig on 2009-08-13
Then why does the initial username created work fine over samba?

---

### Post by mpsrig on 2009-08-13
nevermind,works fine after a couple reboots

---

