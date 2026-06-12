---
title: "Password help"
date: 2010-06-15
forum: General Help
---

### Post by fireslayer on 2010-06-15
still new to ubuntu and i thoroughly enjoy it...the general question i have is that any time i try to make an admin change it asks me for my "key" (password). This started when I changed my original password to a new one. Can someone direct me on how to change this so it doesn't ask me every time for a password.

---

### Post by ThesaurusRex on 2010-06-15
To be blunt: no.

The root password is there for a reason: so we don't screw things up too easily. You always have to put in a root password when making big decisions as an added level of security for your precious computer.

---

### Post by bodhi.zazen on 2010-06-15
> **fireslayer said:**
> still new to ubuntu and i thoroughly enjoy it...the general question i have is that any time i try to make an admin change it asks me for my "key" (password). This started when I changed my original password to a new one. Can someone direct me on how to change this so it doesn't ask me every time for a password.

What password are you asking about ?

This one (keyring)

[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

---

### Post by oldos2er on 2010-06-15
When you change your user password, the gnome keyring is not updated (this is an old bug that doesn't seem to have been fixed). Open menus Applications, Accessories, Passwords and Encryption Keys, right-click on Passwords: login, Change Password, and it should work once you update it with your new password.

---

