---
title: "Can't add user to GADMIN-proftpd"
date: 2011-06-24
forum: General Help
---

### Post by airspoon on 2011-06-24
I have installed proftpd, more specifically "gadmin-proftpd" and it seems to work okay, though only until I try to add a new user. After adding a new user, the status goes to 'deactivated' and when I try to press the activation button, it kicks back this error:
```
 - Fatal: TLSRSACertificateFile: '/etc/gadmin-proftpd/certs/cert.pem' does not exist on line 65 of '/etc/proftpd/proftpd.conf'
```

I went to the config file specified in that error message and line 65 of the proftpd says exactly what the error message says it doesn't. Line 65 says:
```
TLSRSACertificateFile /etc/gadmin-proftpd/certs/cert.pem
```

What I'm ultimately trying to do, is give ftp access to my web director "/var/www/" so that I can upload and change files through an IDE. 

I'm becoming very frustrated with this seemingly basic task, as proftpd (or maybe the gadmin gui?) doesn't want to allow me to do it. I have already installed and removed the gadmin-proftpd package at least 5 times, as every time it "deactivates" after I try to add a user, it stays deactivated -even if I delete the newly created user account.

Surely, there has to be an easier way, right? Any help that anyone could provide would be greatly appreciated. Thanks.

---

