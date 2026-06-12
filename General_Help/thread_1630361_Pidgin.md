---
title: "Pidgin"
date: 2010-11-25
forum: General Help
---

### Post by Drenriza on 2010-11-25
So i setted by my e-mail address that i use with pidgin, to an IMAP google saloution with SSL enabled.

Afterwards i get this, every god damn time it starts up
**The certificate for omega.contacts.msn.com could not be validated. The certificate chain presented is invalid.**

And i have tried several saloutions, to solve this. And nothing works.

Anyone help, please!

kind regards

---

### Post by Helkaluin on 2010-11-25
Update your Pidgin.
See: [http://developer.pidgin.im/wiki/ChangeLog](http://developer.pidgin.im/wiki/ChangeLog)

---

### Post by Drenriza on 2010-11-25
Can you tell me how to update my pidgin without deleting it?

---

### Post by Drenriza on 2010-11-25
```
sudo apt-get upgrade pidgin
```
Solved

---

### Post by Helkaluin on 2010-11-25
You can wait for a few days using the Pidgin PPA: [https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)

Or you can have a look at GetDeb which already delivers the 2.7.7 Pidgin. Note however going the GetDeb route will also update other parts of your system to some potentially unstable versions.

---

