---
title: "Tried to change password; new and old do not authenticate"
date: 2010-01-10
forum: General Help
---

### Post by polarberg on 2010-01-10
This is a doozy.

I tried to change my password through the Users and Groups dialogue, and now neither the old one nor the new one work.

I tried to do it once, and it didn't do anything (the password was still my old password), then the second time I did it, when I went to save the configuration it wouldn't take my new password or my old one. Now I can't authenticate for anything.

A wicked backdoor I've noticed is that going into recovery mode offers you a root console without authentication. (Awesome, Linux, secure as all ****, seriously.) Is there any way to use this to set my user password without needing to authenticate?

---

### Post by michy99 on 2010-01-10
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Basically```
passwd YOUR_USER_NAME
```and you will be prompted for a new password.

---

### Post by polarberg on 2010-01-10
*facepalm*

So, my password doesn't actually protect my computer against a real-life person at all, then. That's...dandy.

Thanks.

---

### Post by Icehuck on 2010-01-10
> **polarberg said:**
> *facepalm*

So, my password doesn't actually protect my computer against a real-life person at all, then. That's...dandy.

Thanks.

If I am sitting in front of your machine then your password is meaningless. It doesn't matter what system you use(osx,windows,unix,linux).

---

### Post by michy99 on 2010-01-10
The only way to protect your data is encryption.

---

### Post by warfacegod on 2010-01-11
> **polarberg said:**
> *facepalm*

So, my password doesn't actually protect my computer against a real-life person at all, then. That's...dandy.

Thanks.

Set a boot password in your BIOS 
(DON'T FORGET WHAT IT IS!)

---

