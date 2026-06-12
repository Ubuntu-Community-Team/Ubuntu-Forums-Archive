---
title: "mod-authnz-ldap authentication"
date: 2011-08-11
forum: General Help
---

### Post by Ow3n on 2011-08-11
Ubuntu 10.10 64-bit server
authnz_ldap enabled

Hey all,

I've been working on this for a while and try as I might, I can't figure it out.

I'm trying to authenticate Apache against my MS Active Directory. I have a Mediawiki installation that I would like to protect with an initial authentication. Here are the contents of the .htaccess file:

   AuthLDAPBindDN "CN=my user,OU=_Users,DC=my_domain,DC=local"
   AuthLDAPBindPassword "my_password"
   AuthLDAPURL "ldap://ldap.my_domain.local/ou=_Users,dc=my_domain,dc=local?sAMAccountName?sub?(objectClass$
   AuthType Basic
   AuthName "Authentication Required"
   AuthBasicProvider ldap
   # Important, otherwise "(9)Bad file descriptor: Could not open password file: (null)"
   AuthUserFile /dev/null
   require valid-user

When browsing to the Mediawiki, I receive the username/pass prompt, but my credentials don't work. Apache reports: " authentication failure for "/mediawiki": Password Mismatch".

If I try the following: ldapsearch -LLL -x -H ldap://ldap.my_domain.local:389 -b 'ou=_Users,dc=my_domain,dc=local' -D 'MY_DOMAIN\my_user' -w 'my_password' '(sAMAccountName)' , I receive "ldap_bind: Invalid credentials (49)  additional info: 80090308: LdapErr: DSID-0C0903A9, comment: AcceptSecurityContext error, data 52e, v1db1.

Is there something wrong with the contents of my .htaccess file? Any help would be appreciated! Thanks.

---

### Post by clubbing80s on 2011-11-30
Hi.
Did you ever resolve this, I'm experiencing similar issues ?

Thanks

---

### Post by galvatron408 on 2011-11-30
f I try the following: ldapsearch -LLL -x -H ldap://ldap.my_domain.local:389 -b 'ou=_Users,dc=my_domain,dc=local' -D 'MY_DOMAIN\my_user' -w 'my_password' '(sAMAccountName)' , I receive "ldap_bind: Invalid credentials (49) additional info: 80090308: LdapErr: DSID-0C0903A9, comment: AcceptSecurityContext error, data 52e, v1db1.

Your binddn is incorrect.

try something like....

ldapsearch -x -h ldap.my_domain.local -b "ou=_Users,dc=my_domain,dc=local" -D "cn=myname,ou=_Users,dc=my_domain,dc=local" -W

when prompted, enter your password. if that doesn't work, install ADSI Edit and if you know what you're doing, you'll be golden. ASDI Edit pretty much exposes the AD tree so that you can just copy and paste. It doesn't get any easier. ([http://technet.microsoft.com/en-us/library/cc773354(WS.10).aspx](http://technet.microsoft.com/en-us/library/cc773354(WS.10).aspx))

From an ex-windows admin, current linux admin and mac os x / ubuntu FAN!
Good Luck!

---

