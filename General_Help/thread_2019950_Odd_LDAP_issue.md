---
title: "Odd LDAP issue"
date: 2012-07-07
forum: General Help
---

### Post by dogriverrat on 2012-07-07
I've got a test Ubuntu 12.04 VM setup with LDAP and I think I've got it setup correctly.  I used a majority of the LDAP stuff from here [https://help.ubuntu.com/12.04/serverguide/serverguide.pdf](https://help.ubuntu.com/12.04/serverguide/serverguide.pdf) as my basis for this.

So I can add users, delete users, search, etc using the LDAP commands and it all seems to work.  The ldapscripts also work.

However, when I try to su to a LDAP account (say from root) I get "Unknown id: <whateverLDAPid>".  This is the logging from an unsuccessful su attempt:

Jul  7 12:42:20 ubuntu slapd[1072]: conn=1023 fd=24 ACCEPT from IP=127.0.0.1:43132 (IP=0.0.0.0:389)
Jul  7 12:42:20 ubuntu slapd[1072]: conn=1023 op=0 BIND dn="cn=admin,dc=ldap,dc=homenet" method=128
Jul  7 12:42:20 ubuntu slapd[1072]: conn=1023 op=0 BIND dn="cn=admin,dc=ldap,dc=homenet" mech=SIMPLE ssf=0
Jul  7 12:42:20 ubuntu slapd[1072]: conn=1023 op=0 RESULT tag=97 err=0 text=
Jul  7 12:42:20 ubuntu slapd[1072]: conn=1023 op=1 SRCH base="dc=ldap,dc=homnet" scope=2 deref=0 filter="(&(objectClass=posixAccount)(uidNumber=-1))"
Jul  7 12:42:20 ubuntu slapd[1072]: conn=1023 op=1 SRCH attr=uid userPassword uidNumber gidNumber cn homeDirectory loginShell gecos description objectClass
Jul  7 12:42:20 ubuntu slapd[1072]: conn=1023 op=1 SEARCH RESULT tag=101 err=32 nentries=0 text=
Jul  7 12:42:20 ubuntu slapd[1072]: conn=1023 op=2 SRCH base="dc=ldap,dc=homnet" scope=2 deref=0 filter="(&(objectClass=posixAccount)(uid=oouser))"
Jul  7 12:42:20 ubuntu slapd[1072]: conn=1023 op=2 SRCH attr=uid userPassword uidNumber gidNumber cn homeDirectory loginShell gecos description objectClass
Jul  7 12:42:20 ubuntu slapd[1072]: conn=1023 op=2 SEARCH RESULT tag=101 err=32 nentries=0 text=
Jul  7 12:42:20 ubuntu slapd[1072]: conn=1023 op=3 UNBIND
Jul  7 12:42:20 ubuntu slapd[1072]: conn=1023 fd=24 closed

The "oouser" account does indeed exist:

ldapsearch -D "cn=admin,dc=ldap,dc=homenet" -w <my password> -h 127.0.0.1 -b "dc=ldap,dc=homenet" -s sub "(&(objectClass=posixAccount)(uid=oouser))" uid userPassword uidNumber gidNumber cn homeDirectory loginShell gecos description objectClass
# extended LDIF
#
# LDAPv3
# base <dc=ldap,dc=homenet> with scope subtree
# filter: (&(objectClass=posixAccount)(uid=oouser))
# requesting: uid userPassword uidNumber gidNumber cn homeDirectory loginShell gecos description objectClass 
#

# oouser, People, ldap.homenet
dn: uid=oouser,ou=People,dc=ldap,dc=homenet
objectClass: account
<snip>

The log for this ldapsearch looks like this:

Jul  7 13:33:32 ubuntu slapd[1072]: conn=1034 fd=24 ACCEPT from IP=127.0.0.1:43146 (IP=0.0.0.0:389)
Jul  7 13:33:32 ubuntu slapd[1072]: conn=1034 op=0 BIND dn="cn=admin,dc=ldap,dc=homenet" method=128
Jul  7 13:33:32 ubuntu slapd[1072]: conn=1034 op=0 BIND dn="cn=admin,dc=ldap,dc=homenet" mech=SIMPLE ssf=0
Jul  7 13:33:32 ubuntu slapd[1072]: conn=1034 op=0 RESULT tag=97 err=0 text=
Jul  7 13:33:32 ubuntu slapd[1072]: conn=1034 op=1 SRCH base="dc=ldap,dc=homenet" scope=2 deref=0 filter="(&(objectClass=posixAccount)(uid=oouser))"
Jul  7 13:33:32 ubuntu slapd[1072]: conn=1034 op=1 SRCH attr=uid userPassword uidNumber gidNumber cn homeDirectory loginShell gecos description objectClass
Jul  7 13:33:32 ubuntu slapd[1072]: conn=1034 op=1 SEARCH RESULT tag=101 err=0 nentries=1 text=
Jul  7 13:33:32 ubuntu slapd[1072]: conn=1034 op=2 UNBIND
Jul  7 13:33:32 ubuntu slapd[1072]: conn=1034 fd=24 closed

The log entries are very similar with the exception of the search initially for "(&(objectClass=posixAccount)(uidNumber=-1))" in the su case.

Attempting to ssh with the "oouser" account also fails with "tag=101 err=32".

Any ideas what my issue is - besides the organic object between the chair and keyboard ?

---

### Post by luvshines on 2012-07-08
I have a dumb question:
Did you just setup the LDAP server only OR your client aswell to work with that LDAP server ?

---

### Post by kimda on 2012-07-08
Did you setup pam to work with ldap (/etc/pam.d) ? And nsswitch.conf?

---

