---
title: "permanently accept certificates for subversion"
date: 2010-02-03
forum: General Help
---

### Post by pokeyThePenguin on 2010-02-03
Every time I use Subversion, I have to accept a certificate and provide my user name and password. I know I can bypass that by specifying --username and --password, but I don't want my password to be in plain view. How can you save the certificate? And is there a way you can authenticate yourself once and not have to provide your log in details from then on when you're using the same computer?

The server is run by the university, so I don't have control over that end, but is there anything I can do from my end?

---

### Post by lovinglinux on 2010-02-03
You can use esvn or kdesvn. The first stores the login info in Gnome Keyring while the second stores it in Kwallet.

---

