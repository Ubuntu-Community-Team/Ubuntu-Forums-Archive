---
title: "ssh-keygen on on behalf of another user"
date: 2012-05-27
forum: General Help
---

### Post by rockballad on 2012-05-27
Hello,

Using root, I can create a new user with its password, e.g. newuser. Then how can I make this user generate a sshkey without logging into it?

Normally, I have to "su newuser", and ssh-keygen -N "". It'll create a sshkey in /home/newuser/.ssh as default with passphrase = empty. 
But now with a script run by root, can I get the same result?

Thank you!

---

### Post by rockballad on 2012-05-27
Oh I can do it, with # su -c "ssh-keygen" newuser. It's so simple.

Thanks anyway!

---

