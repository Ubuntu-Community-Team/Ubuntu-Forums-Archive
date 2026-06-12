---
title: "Remove Guest"
date: 2012-02-15
forum: General Help
---

### Post by Zaphod Newcastle on 2012-02-15
My computer has a guest user account and I'd like to remove it or put a password on it please.

---

### Post by Gremlinzzz on 2012-02-15
:popcorn:

sudo passwd <user>

---

### Post by trollger on 2012-02-15
sudo userdel guest

should remove the account.

---

### Post by Zaphod Newcastle on 2012-02-18
Thank you for the responses. I don't understand what I should do though!

---

### Post by winh8r on 2012-02-18
Press Ctrl + Alt + T

this will open a terminal window

you need to enter the following:

```
sudo userdel -r -f username
```
 Where "username" is the login name of the guest account

So if you wanted to delete Bob as a user you would enter

sudo userdel -r -f Bob


However if you decide to keep Bob as a user and want to set his password you

would enter

sudo passwd Bob

and do it that way.

Hope this helps you!

---

### Post by Zaphod Newcastle on 2012-03-20
Thank you! It now says "user "guest" does not exist"!

---

