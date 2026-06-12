---
title: "Can I turn off password locks?"
date: 2010-08-10
forum: General Help
---

### Post by johnnydangerx2 on 2010-08-10
Hi everyone.  So I am very new to Linux (after many years going by since I last used it) and I have installed Ubuntu as the primary OS on a secondary computer.  This computer is only used for web surfing by my kids and the occasional email check and document viewer.  I want to have a login/account for each person in our house, but its kind of a pain to have to enter a password everytime we want to change a user.  Is there any way to remove the prompt asking for a password or is this something we just have to deal with. I thought just leaving the password field blank when setting up each user would do the trick, but it did not. 


Any help is appreciated.  Thanks.

---

### Post by sisco311 on 2010-08-11
You can allow a user to log in (at least via GDM) without a password by adding it to the *nopasswdlogin* group.
```
sudo gpasswd -a **username** nopasswdlogin
```

---

### Post by johnnydangerx2 on 2010-08-12
Great, thank you. I will try that. 

Do you know if this allows me to switch from user to user without a password prompt?

---

