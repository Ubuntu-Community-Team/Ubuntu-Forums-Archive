---
title: "Skype will not launch"
date: 2011-03-13
forum: General Help
---

### Post by stuart221 on 2011-03-13
I am using Ubuntu 10.10 I get the following massage.
Admin@Ubuntu21:~$ skype: symbol lookup error: /usr/lib/libQtDBus.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv
I have tried reinstalling it but still the same problem.

---

### Post by squaregoldfish on 2011-03-13
I'm assuming you downloaded the Ubuntu package for Skype. This was built for Ubuntu 8.10, which has a different version of QT installed. The version of QT for 10.10 appears to be incompatible with Skype.

The easiest way to get round this is to install the Static version of Skype, which comes with all the required libraries built into it. This should work independently of whatever version of Ubuntu you're using.

Steve.

---

