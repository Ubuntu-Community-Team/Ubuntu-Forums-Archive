---
title: "Help me please!"
date: 2012-03-25
forum: General Help
---

### Post by Alexandru098 on 2012-03-25
I NEED HELP FAST!!!

I installed wubi on my laptop (windows 7), and when i logged in to ubuntu i went to user account and deleted my password, so that i can log in without using it,

But now everytime ubuntu asks me authentificate it asks me a password and whatever i type there i says it's incorrect?

What can i do?

---

### Post by zombifier25 on 2012-03-25
First off, a thread that's only 1 hr old can hardly be considered dead, so don't spam.
Secondly, you should not delete an administrator account's password. If you simply don't want to type your password at login, simply choose to auto login at User Account settings (click on your username on the top panel, chose "User Accounts")
The only way to fix this is to reboot, choose "Recovery Mode", select "Drop to Root Shell Prompt", and type this at the terminal:
```
passwd yourusernamehere
```
Insert your new password.

---

