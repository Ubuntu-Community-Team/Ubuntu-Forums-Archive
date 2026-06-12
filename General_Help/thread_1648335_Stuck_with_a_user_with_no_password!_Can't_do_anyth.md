---
title: "Stuck with a user with no password! Can't do anything! HELP!!!"
date: 2010-12-18
forum: General Help
---

### Post by davidmigl on 2010-12-18
I am about to sell a computer with ubuntu on it, and I created a user with no password and deleted my previous user. Now there is only one user account, and it has a blank password. However, any time I need root access (sudo, configuring user accounts, etc.) the system won't accept a blank password. It just says "authentication failure."

Help!  Deleting my other account was silly. I am stuck with just one user account with a blank password!

---

### Post by sgosnell on 2010-12-18
If you can log on, then just change the password.  ```
passwd user
```then enter a blank for the current password, then enter a new password twice.  That should do it.

---

### Post by davidmigl on 2010-12-19
When I do that I get the message

passwd: Authentication token manipulation error
passwd: password unchanged

when I hit "enter" right after it asks me for the "(current) UNIX password:"

---

### Post by coffeecat on 2010-12-19
You need to boot up in recovery mode before running 'passwd *username*'. Have a look here for comprehensive instructions:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

By the way, the user with the currently blank password: did you ensure that this is an administrator account? If not, you'll need to see this:

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

