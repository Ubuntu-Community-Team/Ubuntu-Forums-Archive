---
title: "ldap authentication problem using uid"
date: 2010-09-16
forum: General Help
---

### Post by snarf77 on 2010-09-16
Hi all,

I'm pretty new to ldap but issue by issue I start understanding more and more things.

One I cant figure out is a problem of authentication. I'm using open ldap server and try to authenticate a groupware (simple groupware) against it. As it fails, I tested with a ldap client to understand things better. 
Using GQ ldap client, I 'm able to browse my ldap tree successfully and to search some args from the base DN i specified. but when entering the exact uid as a search string iI got no answer whereas searching the cn returns the correct entry (and display its related entry including the uid  I can't find ..)

I jsut can't go further myself and come here to ask for help.

Here is the only thing I can trace in logs (syslog) when trying to seach firstname.lastname (= uid)
```
Sep 16 11:43:58 EGW slapd[1112]: conn=1004 op=0 do_bind: invalid dn (firstname.name)
Sep 16 11:44:20 EGW slapd[1112]: <= bdb_substring_candidates: (cn) not indexed
```Here is the ldif file I use for this user (the one I try to log in). The rest of the config (dc, ou...) is an exact copy paste of the openldap tutorial in ubuntu 10.04 server guide (except for domain name and password of course):

```
  
uid=firstname.lastname,ou=people,dc=mycompany,dc=com
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
uid: firstname.lastname
sn: lastname
givenName: firstname
cn: firstname lastname
displayName: firstname lastname
uidNumber: 1001
gidNumber: 10000
userPassword: password
gecos: firstname lastname
loginShell: /bin/bash
homeDirectory: /home/firstname.lastname
shadowExpire: -1
shadowFlag: 0
shadowWarning: 7
shadowMin: 8
shadowMax: 999999
shadowLastChange: 10877
mail: firstname.lastnamel@mycompany.com
postalCode: 12345
l: MyLocation
o: mycompany
mobile: +33 (0)6 xx xx xx xx
homePhone: +33 (0)5 xx xx xx xx
title: Occupation
postalAddress:
initials: AZERTY

```At last when trying to authenticate from my groupware and entering login = firstname.lastname corresponding to uid, I got a "firstname.lastname" not found in database (which I can uderstand as even a ldap client can't find him). When login as firstname, I got a return as name is found in database but login failed (probably password / uid adequation problem ??)

Hope someone can help me as I'm really lost with that.


I forgot the most important. when trying to search the user with :
 sudo ldapsearch -xLLL  -H ldap://ipofmyldapserver/ -b "ou=people,dc=mycompany,dc=com" "uid=firstname.lastname" uid
it returns the correct user and I can see its uid: firstname.lastname

If you need any more information, don't hesitate to ask

Thanks in advance

Snarf

---

### Post by luvshines on 2010-10-06
Maybe I am replying late :D

Still having issue ??

---

