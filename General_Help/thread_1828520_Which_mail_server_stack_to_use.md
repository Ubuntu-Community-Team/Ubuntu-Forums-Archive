---
title: "Which mail server stack to use?"
date: 2011-08-19
forum: General Help
---

### Post by stepheny on 2011-08-19
I have always in the past installed and configured my own mail server with Postfix, Fetchmail, Procmail and Dovecot. I know that for a while the Ubuntu server team have developed their own server stack and so I decided to give it a go with my new 11.04 installation. 

However, when I look on Synaptic I see that there are two mail server stacks
> mail-stack-delivery and > dovecot-postfix. Both are described as > "mail server delivery agent stack provided by the Ubuntu server team"

So, my question is what is the difference between the two stacks?

---

### Post by tcsmith1978 on 2011-08-19
Juts had a look at the packages at:

[http://packages.ubuntu.com/natty/mail-stack-delivery](http://packages.ubuntu.com/natty/mail-stack-delivery)
and
[http://packages.ubuntu.com/natty/dovecot-postfix](http://packages.ubuntu.com/natty/dovecot-postfix)

Worth pointing out that the dovecot-postfix states that "This is a transitional package to support upgrades and may be safely removed after installation."

---

