---
title: "Setting Up LDAP for a Small Business"
date: 2006-06-16
forum: General Help
---

### Post by jrattner on 2006-06-16
Afternoon,

I work in a small office with about twenty people.  What I'm attempting to do is set up a server so that we can all share e-mail contacts.  Each of the computers which will utilize the shared contacts are running Mozilla Thunderbird.

A.) Is LDAP the easiest solution to my problem of sharing e-mail contacts?

B.) How simple is it to set up an LDAP server that simply manages e-mail contacts names, and maybe if I'm lucky real addresses?

C.) If indeed LDAP is the solution, could someone provide me with some information and or links on how to configure/set up my server.  I have already read about client authentication and how to install the server on wiki.ubuntu.com but have found nothing on configuration.

Any help / incites would be appreciated :)

---

### Post by brickbat on 2006-06-16
Hi,

check this out:

[http://times.usefulinc.com/2005/09/25-ldap](http://times.usefulinc.com/2005/09/25-ldap)

---

### Post by AlexPJ on 2006-06-23
I followed this but have clearly done something wrong ..
I can look at the data in ldap (slapcat & ldapsearch), change the passwords with (ldappasswd), add more data with with ldapadd, etc basically the ldap directory works fine.

When I added a new user, uid=alex, to the directory and did "su - alex" the new home directory was created and I became alex! It didn't check the password I guess.  Getent password alex returns the correct stuff, and I have downladed a copy of LDAPmanager ([http://www.ldapmanager.org/](http://www.ldapmanager.org/)) so I know the ssl works.

BUT when I try to login I get:
(ldap.log)
<snip>
Jun 23 13:47:34 boston slapd[4778]: => access_allowed: read access to "uid=alex,ou=People,dc=bpm,dc=local" "userPassword" requested
Jun 23 13:47:34 boston slapd[4778]: <= root access granted
Jun 23 13:47:34 boston slapd[4778]: conn=45 op=2 ENTRY dn="uid=alex,ou=people,dc=bpm,dc=local"
Jun 23 13:47:34 boston slapd[4778]: conn=45 op=2 SEARCH RESULT tag=101 err=0 nentries=1 text=

(auth.log)
Jun 23 13:47:32 boston login[5321]: pam_ldap: error trying to bind (Invalid credentials)
Jun 23 13:47:35 boston login[5321]: FAILED LOGIN (1) on 'tty1' FOR `alex', Authentication service cannot retrieve authentication info.

(pam_ldap.conf)
host    ldap.bpm.local
uri     ldap://ldap.bpm.local
base    dc=bpm,dc=local
ldap_version 3
rootbinddn cn=ldaproot,dc=bpm,dc=local
pam_password exop

Please if you have any idea where I'm going wrong (pretty) please let me know!  It's clearly looking for the password and found it but something goes wrong in the communication.  The password is stored in {SSHA} form by ldappassword .. couldn't be trying to match it with a {CRYPT} could it?

Thank you

Al.](*,)

---

### Post by AlexPJ on 2006-06-23
Finally sorted it out I think.. I can login now using the ldap user.

I think it had somethitng to do with the hashing not being comparable:
[http://hannibal.solstice.nl/hannibal-3.0_on-debian-sarge_2005-04-03.html](http://hannibal.solstice.nl/hannibal-3.0_on-debian-sarge_2005-04-03.html)
This finally sorted it out - I more or less copied the /etc/libnss-ldap.conf and /etc/pam_ldap.conf files and suddenly it works!

The only real differnce is the md5 in the various places.  I'll have to figure out why they make it work at some later time!  I've been stuck here for a week or so so I'm just glad it works!

Al.

---

