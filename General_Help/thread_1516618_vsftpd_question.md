---
title: "vsftpd question"
date: 2010-06-24
forum: General Help
---

### Post by zetharx on 2010-06-24
This may apply to any FTP daemon, but I am running vsftpd.  Is there any way for me to automatically chown files uploaded by only one specific account??  I do not want all things chowned, only files uploaded by one account.

Also, is there a way to have a different local_umask for different accounts?

I just have one account which I want to behave differently then regular user accounts, and a helpful answer to either of these questions could get me where I want to be.  Thanks a lot.

---

### Post by Leppie on 2010-06-24
you want to have a look at this article: [http://www.enterprisenetworkingplanet.com/nethub/article.php/3377351/In-a-DNS-bind-Get-Out-With-dnsmasq.htm](http://www.enterprisenetworkingplanet.com/nethub/article.php/3377351/In-a-DNS-bind-Get-Out-With-dnsmasq.htm)

---

### Post by zetharx on 2010-06-25
i've looked at it but forgive me for not seeing the relevance to my question.

---

### Post by Leppie on 2010-06-25
i am sorry about the link, must've gone wrong pasting it.
i was reading something about changing owner and setting umasks for vsftpd...

---

