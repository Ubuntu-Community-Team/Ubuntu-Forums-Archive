---
title: "LDAP Application Authentication"
date: 2012-06-28
forum: General Help
---

### Post by freshgrilled on 2012-06-28
First time posting on this forum, so feel free to nudge me in the right direction if I'm posting this in the wrong area.

I've been attempting to deploy openldap (cn=config) across our cloud environment.  

The version is openldap 2.4.2 and I'll paste the contents of the exported ldif at the end of this.

I'm attempting to configure openldap so that applications can connect and authorize users.  Some examples, I've got Atlassian products, zabbix, Nexus, and a few other items that are all ldap friendly.

I've configured ldap and configured just enough accounts to attempt some tests.  Everything seems to test ok with ldapsearch, and using nexus (for example) I can test authentication via the admin account and the application finds and lists users properly from the ldap application.

This is great, but after configuring the various applications with ldap and the users, I am unable to log in as any of the users.  In nexus, I used the application to add the user (after it found the user via ldap) and added a local permission set that allowed log on, but no go.  No errors in the logs either.  A kneejerk reaction on my part has been to assume the password was not configured correctly, but I've fiddled with the password and have not been able to resolve the problem.

I have done some research, but most documentation is for older pre cn=config (not that I'm sure that matters with regards to my issue) and looking up authentication issues with ldap almost always either results in information advanced authentication or local system account authentication (which I am not using).

By default I am using a plaintext password (userPassword)

Some raw info (passwords and names have been modified)

Here is the result of an ldap search:

root@ip-10-122-114-98:/etc/ldap/slapd.d/cn=config# ldapsearch -D cn=admin,dc=inside,dc=com -w naughy -b ou=users,dc=inside,dc=com uid=john
# extended LDIF
#
# LDAPv3
# base <ou=users,dc=inside,dc=com> with scope subtree
# filter: uid=john
# requesting: ALL
#

# John Paul, users, inside.com
dn: cn=John Paul,ou=users,dc=inside,dc=com
objectClass: inetOrgPerson
objectClass: organizationalPerson
objectClass: person
objectClass: top
uid: john
sn: Paul
cn: John Paul
userPassword:: ZXpwymVlczA=
mail: [email]john@inside.com[/email]

# search result
search: 2
result: 0 Success

# numResponses: 2
# numEntries: 1

------------------------

Contents of LDIF
version: 1

dn: dc=inside,dc=com
objectClass: domain
dc: inside

dn: ou=users,dc=inside,dc=com
objectClass: top
objectClass: organizationalUnit
ou: users

dn: ou=groups,dc=inside,dc=com
objectClass: top
objectClass: organizationalUnit
ou: groups

dn: cn=John Paul,ou=users,dc=inside,dc=com
objectClass: top
objectClass: person
objectClass: organizationalPerson
objectClass: inetOrgPerson
cn: John Paul
sn: Paul
mail: removed
uid: john
userPassword:: ZXhafeVeafA=

dn: cn=admin,ou=groups,dc=inside,dc=com
objectClass: top
objectClass: groupOfUniqueNames
cn: admin
uniqueMember: uid=john,ou=users,dc=inside,dc=com

dn: cn=Developer,ou=users,dc=inside,dc=com
objectClass: top
objectClass: person
objectClass: organizationalPerson
objectClass: inetOrgPerson
cn: Developer
sn: Developer
mail: removed
uid: dev
userPassword:: MXZfMGQsfTBafeN5

dn: cn=developers,ou=groups,dc=inside,dc=com
objectClass: top
objectClass: groupOfUniqueNames
cn: developers
uniqueMember: uid=erik,ou=users,dc=inside,dc=com
uniqueMember: uid=john,ou=users,dc=inside,dc=com
uniqueMember: uid=dev,ou=users,dc=inside,dc=com

dn: cn=Erik Aryan,ou=users,dc=inside,dc=com
objectClass: top
objectClass: person
objectClass: organizationalPerson
objectClass: inetOrgPerson
cn: Erik Aryan
sn: Aryan
mail: removed
uid: eric
userPassword:: ZW5sfWtvMafdMiE=

---

