---
title: "How to configure Sylpheed to use a server LDAP using SSL"
date: 2012-01-18
forum: General Help
---

### Post by Luca Borrione on 2012-01-18
I'm using Entic.net as a free online service of server LDAP (I don't know if there are other free cohices).

Here you can find the documentation to configure the client in order to use the service
[http://wiki.entic.net/doku.php?id=cloudface]("http://wiki.entic.net/doku.php?id=cloudface")

I'm using Sylpheed as email client and sadly there's no documentation for it :(

Anyhow, playing around, I found a way to correctly configure it, using:

Hostname: ds1-sjc.entic.net
Port number: 636
Base DN: uid=, ou=people, o=entic.net
Bind DN: uid=, ou=people, o=entic.net
Bind password: Search: (&(mail=)(cn=%s))

Now, **the problem is** that this configuration works great at home, while not at office :(

So, on the office machine, I tried to configure Thunderbird using the above documentation and it works perfectly.
I looked at the other email clients configuration too and I think that the only difference is
[COLOR="Red"]that they all check a checkbox to use secure connection (SSL)
while in Sylpheed I don't have any checkbox like that[/COLOR].

**Is there anyone knowing how to tell Sylpheed to use SSL with a LDAP Server?**

I'm using Sylpheed 3.2.0beta3 (Build 1122) on Lubuntu Oneiric

Thank you all for any suggestion

---

### Post by Rodney9 on 2012-01-18
If you still want a lightweight email program and not use Thunderbird, you could try Claws, available in Synaptic.

Claws uses SSL over POP3, SMTP, IMAP4rev1 and NNTP protocols

more features  - [http://www.claws-mail.org/features.php](http://www.claws-mail.org/features.php)

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

