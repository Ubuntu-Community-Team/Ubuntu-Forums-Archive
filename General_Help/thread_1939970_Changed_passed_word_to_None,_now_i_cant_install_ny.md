---
title: "Changed passed word to None, now i cant install nything"
date: 2012-03-12
forum: General Help
---

### Post by joecowan27 on 2012-03-12
i changed my pass word to 'none' n now i cant instal nything. 
i know this is to do with the root password but i have no idea wat my root password is. 
ive entering the pasword i set during instalition but it dosnt work.
if nyone has any ideas how to sort this out that would great.

---

### Post by Frogs Hair on 2012-03-12
Hello and Welcome

You can look at the link , but without knowing how you removed the need for a password I don't know if it will help . If you simply set an automatic login that can be changed from User Accounts .

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Prescilla on 2012-05-11
> **joecowan27 said:**
> i changed my pass word to 'none' n now i cant instal nything. 
i know this is to do with the root password but i have no idea wat my root password is. 
ive entering the pasword i set during instalition but it dosnt work.
if nyone has any ideas how to sort this out that would great.
That means you may probably have enabled automatic login.

Open a terminal by pressing Alt+Ctrl+T and type:
passwd
Enter your new password.
Confirm it.
Then you have a new password and you'll be able to do installs and updates.

Hope that helps

---

