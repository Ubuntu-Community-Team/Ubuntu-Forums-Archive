---
title: "Ubuntu 9.10 &lt;-&gt; debian-edu-Mainserver"
date: 2010-01-09
forum: General Help
---

### Post by Lebowski1 on 2010-01-09
Hallo,
is there someone how tried to bind an Ubuntu 9.10 (or Edubuntu) Client/Workstation to an debian-edu (etch) Mainserver?
I found an HowTo here: [http://www.mail-archive.com/edubuntu-devel@lists.ubuntu.com/msg02991.html](http://www.mail-archive.com/edubuntu-devel@lists.ubuntu.com/msg02991.html) but it only works till Feisty.
If you do it this way on Ubuntu Karmic:
```
getent passwd
```you will see all ldap-users, but 'su <username>'  doesn't work
```

su <username>
Password:
su: authentication failure

```So, i think there is a problem with PAM. But i don't know where.
Here are some interesting files:
----------------
auth.log
```
Jan  4 21:25:19 rootgym-laptop login[2838]: pam_unix(login:auth): authentication failure; logname=rootgym uid=0 euid=0 tty=/dev/pts/2 ruser= rhost=  user=mschulte
Jan  4 21:25:19 rootgym-laptop login[2838]: pam_ldap: error trying to bind as user "uid=mschulte,ou=People,dc=skole,dc=skolelinux,dc=no" (Confidentiality required)
Jan  4 21:25:21 rootgym-laptop login[2838]: FAILED LOGIN (2) on '/dev/pts/2' FOR 'mschulte', Authentication failure
Jan  4 21:25:29 rootgym-laptop login[2838]: pam_ldap: error trying to bind as user "uid=mschulte,ou=People,dc=skole,dc=skolelinux,dc=no" (Confidentiality required)
Jan  4 21:25:31 rootgym-laptop login[2838]: FAILED LOGIN (3) on '/dev/pts/2' FOR 'mschulte', Authentication failure
```-------------------
```

:~# grep -v '#' /etc/**pam_ldap.conf** |sort -u

base ou=People,dc=skole,dc=skolelinux,dc=no
host ldap
ldap_version 3
pam_filter objectclass=posixAccount
pam_password exop
ssl start_tls

```----------------------
```

:~# grep -v '#' /etc/ldap/**ldap.conf** |sort -u

BASE    dc=skole,dc=skolelinux,dc=no
HOST ldap
TLS_CACERT /etc/ldap/ssl/ldap-server-pubkey.pem
TLS_REQCERT never

```I also tried TLS_REQCERT allow
-----------------------

Thanks, Martin

---

