---
title: "Many LDAP connections"
date: 2010-11-04
forum: General Help
---

### Post by Jyda on 2010-11-04
My user account is autheticated against an LDAP server. Looking through my network connections, I see a large amount of persistant connections.

There is a total of about 70 connections going on at the same time from different processes. This is an abbreviated list of the connections:

[FONT="Courier New"]cupsd 1329 root myclient:36850->ldapserver:ldap (ESTABLISHED)
gvfsd-tra 3161 myaccount myclient:36844->ldapserver:ldap (ESTABLISHED)
bash 2950 myaccount myclient:36793->ldapserver:ldap (ESTABLISHED)
chrome 3085 myaccount myclient:36856->ldapserver:ldap (ESTABLISHED)
kwin 2819 myaccount myclient:36752->ldapserver:ldap (ESTABLISHED)
okular 2982 myaccount myclient:36831->ldapserver:ldap (ESTABLISHED)
ubuntu-ss 3309 myaccount myclient:36875->ldapserver:ldap (ESTABLISHED)
gvfs-fuse 3074 myaccount myclient:36839->ldapserver:ldap (ESTABLISHED)
chrome 3501 myaccount myclient:36945->ldapserver:ldap (ESTABLISHED)
akonadi_n 2881 myaccount myclient:36762->ldapserver:ldap (ESTABLISHED)
okular 2977 myaccount myclient:36832->ldapserver:ldap (ESTABLISHED)
gconf-hel 2935 myaccount myclient:36781->ldapserver:ldap (ESTABLISHED)
akonadi_m 2880 myaccount myclient:36761->ldapserver:ldap (ESTABLISHED)
kmix 2947 myaccount myclient:36799->ldapserver:ldap (ESTABLISHED)
bash 2972 myaccount myclient:36822->ldapserver:ldap (ESTABLISHED)
gdm-simpl 2352 root myclient:36737->ldapserver:ldap (ESTABLISHED)
.
.
.[/FONT]

What's up with that?

I'm running Ubuntu 10.10.

---

