---
title: "Getting Domain name"
date: 2009-08-07
forum: General Help
---

### Post by satish_j on 2009-08-07
How can one get the Domain name of a standalone Ubuntu system.Iam trying to send a mail through sendmail manually using verbose:
```

/usr/sbin/sendmail -v abcd@xyz.com

```
And,i get the error as **"local host name['ddffdf']is not qualified".**
I found that this error is due to Domain name not specified in /etc/hosts file.
At the time of installing,i specified only the hostname.How can i now get the Domain name of my system.
Pls help..

---

### Post by credobyte on 2009-08-07
Your system does not have a domain name - all it has is a hostname ( see [http://www.raffar.com/checkip/](http://www.raffar.com/checkip/) ).

---

### Post by satish_j on 2009-08-07
that is what iam asking..How can i get the Domain name??

---

### Post by credobyte on 2009-08-07
> **satish_j said:**
> that is what iam asking..How can i get the Domain name??

[http://www.godaddy.com/](http://www.godaddy.com/) :D

---

### Post by satish_j on 2009-08-07
that means i have shell out money for getting domain name.:confused:
Iam just testing the sendmail.Is there any free way by which it can be done.:(

---

### Post by credobyte on 2009-08-07
> **satish_j said:**
> that means i have shell out money for getting domain name.:confused:
Iam just testing the sendmail.Is there any free way by which it can be done.:(

Try [No-IP]("http://www.no-ip.com/") ( tough, I'm not sure if it'll be enough .. haven't used *sendmail* ).

---

