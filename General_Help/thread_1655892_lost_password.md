---
title: "lost password"
date: 2010-12-30
forum: General Help
---

### Post by dennisofnewport on 2010-12-30
Ok I just got my self in a mess. I wanted to change a users password and some how changed mine instead. I am the administrator. (go figure) now I can only log on to the users account
I tried old password
I tried no password
I tried users password

No luck all failed. I am off to work so will not be able to respond until tonight so I hope you guys have a few tricks up your sleeve. Thanks.

---

### Post by mcduck on 2010-12-30
Easy fix. :)

Select the recovery mode from Grub menu, and choose the root shell when asked what you want to do. Once there you can just run "passwd *username*" and then set the new password. (replace *username* with your actual user name of course).

---

### Post by dennisofnewport on 2010-12-30
thank you for your help. it worked. There was one step missind "drop to root shell promt" once there I could reset password.

---

