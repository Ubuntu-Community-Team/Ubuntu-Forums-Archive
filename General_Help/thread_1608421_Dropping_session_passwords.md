---
title: "Dropping session passwords"
date: 2010-10-29
forum: General Help
---

### Post by lviggiani on 2010-10-29
Hi everybody,
I've a "stupid" question.
When I connect to a smb share through nautilus it asks me the user name and password and it offers three options:
1) Forget the password immediately
2) Keep the password until the session is ended
3) Remember forever

Let's imagine I choose option 2: How can I "forget" the previously entered username and password when I try to connect again to that share, so that the system will ask a new one, without having to log-off and login again?
Thanks in advance,
Luca.

---

### Post by yetiman64 on 2010-10-29
> **lviggiani said:**
> Hi everybody,
I've a "stupid" question.
When I connect to a smb share through nautilus it asks me the user name and password and it offers three options:
1) Forget the password immediately
2) Keep the password until the session is ended
3) Remember forever

Let's imagine I choose option 2: How can I "forget" the previously entered username and password when I try to connect again to that share, so that the system will ask a new one, without having to log-off and login again?
Thanks in advance,
Luca.
Before connecting to the share, look in Applications > Accessories > Password and Encryption Keys > Passwords, and expand Passwords:login and check for a smb related entry. You can right click it and check in the properties to ensure it is the one you want and if necessary even delete it from there prior to reconnecting to the share (at which time you should be asked for the password again as it is no longer in the keyring).

I have used this when in the past I have used option 3 (Remember Forever) but am not sure if it is the same for sessions (option 2). It would pay for you to experiment a bit with it and check before relying on this info.

---

### Post by lviggiani on 2010-10-29
Hi Thanks for your suggestion...
I had already checked in my keyring but there it saves only when you select "remember forever", as in your experience.
I guess that "session only" passwords are kept somewhere else or handled by nautilus directly.

> **yetiman64 said:**
> Before connecting to the share, look in Applications > Accessories > Password and Encryption Keys > Passwords, and expand Passwords:login and check for a smb related entry. You can right click it and check in the properties to ensure it is the one you want and if necessary even delete it from there prior to reconnecting to the share (at which time you should be asked for the password again as it is no longer in the keyring).

I have used this when in the past I have used option 3 (Remember Forever) but am not sure if it is the same for sessions (option 2). It would pay for you to experiment a bit with it and check before relying on this info.

---

