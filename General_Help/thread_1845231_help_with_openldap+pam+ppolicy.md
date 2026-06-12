---
title: "help with openldap+pam+ppolicy"
date: 2011-09-16
forum: General Help
---

### Post by noussa on 2011-09-16
Hi every one
i use open ldap for ubunt's authetification with pam.
I want to use ppolicy to ask user changing his password after password reset by openldap admin.
this doesn't work for me
the policy seems not been used :(
I tried too much guide but they didn't be helpfull :(
The user never had been asked to change his password :(
any idea plz?

---

### Post by noussa on 2011-09-18
i think that the problem is solved :)
just you have to fusu on the class that we are using in the policies:
it must be like that :
dn: cn=Password,ou=Policies,dc=test,dc=org
cn: Password
sn: Password
[B]objectClass: top
objectClass: person
objectClass: pwdPolicy
objectClass: pwdPolicyChecker[/B]
pwdAttribute: 2.5.4.35
pwdAllowUserChange: TRUE
pwdMustChange: TRUE

dont froget to deleet use_authok from common-passwordafter affecting the policy to the user, the system will ask the user to change his password :)
that's it ;)

---

### Post by noussa on 2011-09-19
this is a copy of mu config files
  	 	 	 	h2 { margin-bottom: 0.11cm; }h2.western { font-family: "Arial",sans-serif; font-size: 14pt; font-style: italic; }h2.cjk { font-family: "DejaVu Sans"; font-size: 14pt; font-style: italic; }h2.ctl { font-family: "Arial",sans-serif; font-size: 14pt; font-style: italic; }p { margin-bottom: 0.21cm; }  **  [COLOR=#000000]pam.d/common-account[/COLOR]**

 [FONT=arial, sans-serif]# [/FONT] 
 [FONT=arial, sans-serif]# /etc/pam.d/common-account - authorization settings common to all services [/FONT] 
 [FONT=arial, sans-serif]# [/FONT] 
 [FONT=arial, sans-serif]# This file is included from other service-specific PAM config files, [/FONT] 
 [FONT=arial, sans-serif]# and should contain a list of the authorization modules that define [/FONT] 
 [FONT=arial, sans-serif]# the central access policy for use on the system.  The default is to [/FONT] 
 [FONT=arial, sans-serif]# only deny service to users whose accounts are expired in /etc/shadow. [/FONT] 
 [FONT=arial, sans-serif]# [/FONT] 
 [FONT=arial, sans-serif]# As of pam 1.0.1-6, this file is managed by pam-auth-update by default. [/FONT] 
 [FONT=arial, sans-serif]# To take advantage of this, it is recommended that you configure any [/FONT] 
 [FONT=arial, sans-serif]# local modules either before or after the default block, and use [/FONT] 
 [FONT=arial, sans-serif]# pam-auth-update to manage selection of other modules.  See [/FONT] 
 [FONT=arial, sans-serif]# pam-auth-update(8) for details. [/FONT] 
 [FONT=arial, sans-serif]# [/FONT] 
 

 [FONT=arial, sans-serif]# here are the per-package modules (the "Primary" block) [/FONT] 
 [FONT=arial, sans-serif]#account	[success=2 new_authtok_reqd=done default=ignore]	pam_unix.so [/FONT] 
 [FONT=arial, sans-serif]#account	[success=1 default=ignore]	pam_ldap.so [/FONT] 
 [FONT=arial, sans-serif]# here's the fallback if no module succeeds [/FONT] 
 [FONT=arial, sans-serif]#account	requisite			pam_deny.so [/FONT] 
 [FONT=arial, sans-serif]# prime the stack with a positive return value if there isn't one already; [/FONT] 
 [FONT=arial, sans-serif]# this avoids us returning an error just because nothing sets a success code [/FONT] 
 [FONT=arial, sans-serif]# since the modules above will each just jump around [/FONT] 
 [FONT=arial, sans-serif]account	required			pam_permit.so [/FONT] 
 [FONT=arial, sans-serif]# and here are more per-package modules (the "Additional" block) [/FONT] 
 [FONT=arial, sans-serif]# end of pam-auth-update config [/FONT] 
 [FONT=arial, sans-serif]account [success=1 default=ignore] pam_unix.so [/FONT] 
 [FONT=arial, sans-serif]account required pam_ldap.so [/FONT] 
 [FONT=arial, sans-serif]account required pam_permit.so[/FONT]
 

 **  [COLOR=#000000]common-account-ldap (if exists)[/COLOR]**

 [FONT=arial, sans-serif]# [/FONT] 
 [FONT=arial, sans-serif]# /etc/pam.d/common-account - authorization settings common to all services [/FONT] 
 [FONT=arial, sans-serif]# [/FONT] 
 [FONT=arial, sans-serif]# This file is included from other service-specific PAM config files, [/FONT] 
 [FONT=arial, sans-serif]# and should contain a list of the authorization modules that define [/FONT] 
 [FONT=arial, sans-serif]# the central access policy for use on the system.  The default is to [/FONT] 
 [FONT=arial, sans-serif]# only deny service to users whose accounts are expired in /etc/shadow. [/FONT] 
 [FONT=arial, sans-serif]# [/FONT] 
 [FONT=arial, sans-serif]# As of pam 1.0.1-6, this file is managed by pam-auth-update by default. [/FONT] 
 [FONT=arial, sans-serif]# To take advantage of this, it is recommended that you configure any [/FONT] 
 [FONT=arial, sans-serif]# local modules either before or after the default block, and use [/FONT] 
 [FONT=arial, sans-serif]# pam-auth-update to manage selection of other modules.  See [/FONT] 
 [FONT=arial, sans-serif]# pam-auth-update(8) for details. [/FONT] 
 [FONT=arial, sans-serif]# [/FONT] 
 

 [FONT=arial, sans-serif]# here are the per-package modules (the "Primary" block) [/FONT] 
 [FONT=arial, sans-serif]#account	[success=2 new_authtok_reqd=done default=ignore]	pam_unix.so [/FONT] 
 [FONT=arial, sans-serif]#account	[success=1 default=ignore]	pam_ldap.so [/FONT] 
 [FONT=arial, sans-serif]# here's the fallback if no module succeeds [/FONT] 
 [FONT=arial, sans-serif]#account	requisite			pam_deny.so [/FONT] 
 [FONT=arial, sans-serif]# prime the stack with a positive return value if there isn't one already; [/FONT] 
 [FONT=arial, sans-serif]# this avoids us returning an error just because nothing sets a success code [/FONT] 
 [FONT=arial, sans-serif]# since the modules above will each just jump around [/FONT] 
 [FONT=arial, sans-serif]#account	required			pam_permit.so [/FONT] 
 [FONT=arial, sans-serif]# and here are more per-package modules (the "Additional" block) [/FONT] 
 [FONT=arial, sans-serif]# end of pam-auth-update config[/FONT]
 

 **  [COLOR=#000000]common-auth[/COLOR]**

 [FONT=arial, sans-serif]# [/FONT] 
 [FONT=arial, sans-serif]# /etc/pam.d/common-auth - authentication settings common to all services [/FONT] 
 [FONT=arial, sans-serif]# [/FONT] 
 [FONT=arial, sans-serif]# This file is included from other service-specific PAM config files, [/FONT] 
 [FONT=arial, sans-serif]# and should contain a list of the authentication modules that define [/FONT] 
 [FONT=arial, sans-serif]# the central authentication scheme for use on the system [/FONT] 
 [FONT=arial, sans-serif]# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the [/FONT] 
 [FONT=arial, sans-serif]# traditional Unix authentication mechanisms. [/FONT] 
 [FONT=arial, sans-serif]# [/FONT] 
 [FONT=arial, sans-serif]# As of pam 1.0.1-6, this file is managed by pam-auth-update by default. [/FONT] 
 [FONT=arial, sans-serif]# To take advantage of this, it is recommended that you configure any [/FONT] 
 [FONT=arial, sans-serif]# local modules either before or after the default block, and use [/FONT] 
 [FONT=arial, sans-serif]# pam-auth-update to manage selection of other modules.  See [/FONT] 
 [FONT=arial, sans-serif]# pam-auth-update(8) for details. [/FONT] 
 

 [FONT=arial, sans-serif]# here are the per-package modules (the "Primary" block) [/FONT] 
 [FONT=arial, sans-serif]auth	required                        pam_group.so use_first_pass [/FONT] 
 [FONT=arial, sans-serif]auth	[success=2 default=ignore]	pam_unix.so nullok_secure try_first_pass [/FONT] 
 [FONT=arial, sans-serif]auth	[success=1 default=ignore]	pam_ldap.so use_first_pass [/FONT] 
 [FONT=arial, sans-serif]# here's the fallback if no module succeeds [/FONT] 
 [FONT=arial, sans-serif]auth	requisite			pam_deny.so [/FONT] 
 [FONT=arial, sans-serif]# prime the stack with a positive return value if there isn't one already; [/FONT] 
 [FONT=arial, sans-serif]# this avoids us returning an error just because nothing sets a success code [/FONT] 
 [FONT=arial, sans-serif]# since the modules above will each just jump around [/FONT] 
 [FONT=arial, sans-serif]auth	required			pam_permit.so [/FONT] 
 [FONT=arial, sans-serif]# and here are more per-package modules (the "Additional" block) [/FONT] 
 [FONT=arial, sans-serif]#auth	optional			pam_smbpass.so migrate [/FONT] 
 [FONT=arial, sans-serif]# end of pam-auth-update config [/FONT] 
 [FONT=arial, sans-serif]#auth required    pam_access.so [/FONT] 
 

 **  [COLOR=#000000]common-auth-ldap(if exists)[/COLOR]**

 [FONT=arial, sans-serif]# [/FONT] 
 [FONT=arial, sans-serif]# /etc/pam.d/common-auth - authentication settings common to all services [/FONT] 
 [FONT=arial, sans-serif]# [/FONT] 
 [FONT=arial, sans-serif]# This file is included from other service-specific PAM config files, [/FONT] 
 [FONT=arial, sans-serif]# and should contain a list of the authentication modules that define [/FONT] 
 [FONT=arial, sans-serif]# the central authentication scheme for use on the system [/FONT] 
 [FONT=arial, sans-serif]# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the [/FONT] 
 [FONT=arial, sans-serif]# traditional Unix authentication mechanisms. [/FONT] 
 [FONT=arial, sans-serif]# [/FONT] 
 [FONT=arial, sans-serif]# As of pam 1.0.1-6, this file is managed by pam-auth-update by default. [/FONT] 
 [FONT=arial, sans-serif]# To take advantage of this, it is recommended that you configure any [/FONT] 
 [FONT=arial, sans-serif]# local modules either before or after the default block, and use [/FONT] 
 [FONT=arial, sans-serif]# pam-auth-update to manage selection of other modules.  See [/FONT] 
 [FONT=arial, sans-serif]# pam-auth-update(8) for details. [/FONT] 
 

 [FONT=arial, sans-serif]# here are the per-package modules (the "Primary" block) [/FONT] 
 [FONT=arial, sans-serif]auth	required                        pam_group.so use_first_pass [/FONT] 
 [FONT=arial, sans-serif]auth	[success=2 default=ignore]	pam_unix.so nullok_secure try_first_pass [/FONT] 
 [FONT=arial, sans-serif]auth	[success=1 default=ignore]	pam_ldap.so use_first_pass [/FONT] 
 [FONT=arial, sans-serif]# here's the fallback if no module succeeds [/FONT] 
 [FONT=arial, sans-serif]auth	requisite			pam_deny.so [/FONT] 
 [FONT=arial, sans-serif]# prime the stack with a positive return value if there isn't one already; [/FONT] 
 [FONT=arial, sans-serif]# this avoids us returning an error just because nothing sets a success code [/FONT] 
 [FONT=arial, sans-serif]# since the modules above will each just jump around [/FONT] 
 [FONT=arial, sans-serif]auth	required			pam_permit.so [/FONT] 
 [FONT=arial, sans-serif]# and here are more per-package modules (the "Additional" block) [/FONT] 
 [FONT=arial, sans-serif]#auth	optional			pam_smbpass.so migrate [/FONT] 
 [FONT=arial, sans-serif]# end of pam-auth-update config[/FONT]
 

 **  [COLOR=#000000]common-password[/COLOR]**

 [FONT=arial, sans-serif]# [/FONT] 
 [FONT=arial, sans-serif]# /etc/pam.d/common-password - password-related modules common to all services [/FONT] 
 [FONT=arial, sans-serif]# [/FONT] 
 [FONT=arial, sans-serif]# This file is included from other service-specific PAM config files, [/FONT] 
 [FONT=arial, sans-serif]# and should contain a list of modules that define the services to be [/FONT] 
 [FONT=arial, sans-serif]# used to change user passwords.  The default is pam_unix. [/FONT] 
 

 [FONT=arial, sans-serif]# Explanation of pam_unix options: [/FONT] 
 [FONT=arial, sans-serif]# [/FONT] 
 [FONT=arial, sans-serif]# The "sha512" option enables salted SHA512 passwords.  Without this option, [/FONT] 
 [FONT=arial, sans-serif]# the default is Unix crypt.  Prior releases used the option "md5". [/FONT] 
 [FONT=arial, sans-serif]# [/FONT] 
 [FONT=arial, sans-serif]# The "obscure" option replaces the old `OBSCURE_CHECKS_ENAB' option in [/FONT] 
 [FONT=arial, sans-serif]# login.defs. [/FONT] 
 [FONT=arial, sans-serif]# [/FONT] 
 [FONT=arial, sans-serif]# See the pam_unix manpage for other options. [/FONT] 
 

 [FONT=arial, sans-serif]# As of pam 1.0.1-6, this file is managed by pam-auth-update by default. [/FONT] 
 [FONT=arial, sans-serif]# To take advantage of this, it is recommended that you configure any [/FONT] 
 [FONT=arial, sans-serif]# local modules either before or after the default block, and use [/FONT] 
 [FONT=arial, sans-serif]# pam-auth-update to manage selection of other modules.  See [/FONT] 
 [FONT=arial, sans-serif]# pam-auth-update(8) for details. [/FONT] 
 

 [FONT=arial, sans-serif]# here are the per-package modules (the "Primary" block) [/FONT] 
 [FONT=arial, sans-serif]password	[success=2 default=ignore]	pam_unix.so obscure sha512 [/FONT] 
 [FONT=arial, sans-serif]password	[success=1 user_unknown=ignore default=die]	pam_ldap.so  try_first_pass [/FONT] 
 [FONT=arial, sans-serif]# here's the fallback if no module succeeds [/FONT] 
 [FONT=arial, sans-serif]password	requisite			pam_deny.so [/FONT] 
 [FONT=arial, sans-serif]# prime the stack with a positive return value if there isn't one already; [/FONT] 
 [FONT=arial, sans-serif]# this avoids us returning an error just because nothing sets a success code [/FONT] 
 [FONT=arial, sans-serif]# since the modules above will each just jump around [/FONT] 
 [FONT=arial, sans-serif]password	required			pam_permit.so [/FONT] 
 [FONT=arial, sans-serif]# and here are more per-package modules (the "Additional" block) [/FONT] 
 [FONT=arial, sans-serif]#password	optional			pam_smbpass.so nullok  use_first_pass [/FONT] 
 [FONT=arial, sans-serif]password	optional	pam_gnome_keyring.so [/FONT] 
 [FONT=arial, sans-serif]# end of pam-auth-update config[/FONT]
 

 ** [COLOR=#000000]common-password-ldap (if exists)[/COLOR]**

 [FONT=arial, sans-serif]# [/FONT] 
 [FONT=arial, sans-serif]# /etc/pam.d/common-password - password-related modules common to all services [/FONT] 
 [FONT=arial, sans-serif]# [/FONT] 
 [FONT=arial, sans-serif]# This file is included from other service-specific PAM config files, [/FONT] 
 [FONT=arial, sans-serif]# and should contain a list of modules that define the services to be [/FONT] 
 [FONT=arial, sans-serif]# used to change user passwords.  The default is pam_unix. [/FONT] 
 

 [FONT=arial, sans-serif]# Explanation of pam_unix options: [/FONT] 
 [FONT=arial, sans-serif]# [/FONT] 
 [FONT=arial, sans-serif]# The "sha512" option enables salted SHA512 passwords.  Without this option, [/FONT] 
 [FONT=arial, sans-serif]# the default is Unix crypt.  Prior releases used the option "md5". [/FONT] 
 [FONT=arial, sans-serif]# [/FONT] 
 [FONT=arial, sans-serif]# The "obscure" option replaces the old `OBSCURE_CHECKS_ENAB' option in [/FONT] 
 [FONT=arial, sans-serif]# login.defs. [/FONT] 
 [FONT=arial, sans-serif]# [/FONT] 
 [FONT=arial, sans-serif]# See the pam_unix manpage for other options. [/FONT] 
 

 [FONT=arial, sans-serif]# As of pam 1.0.1-6, this file is managed by pam-auth-update by default. [/FONT] 
 [FONT=arial, sans-serif]# To take advantage of this, it is recommended that you configure any [/FONT] 
 [FONT=arial, sans-serif]# local modules either before or after the default block, and use [/FONT] 
 [FONT=arial, sans-serif]# pam-auth-update to manage selection of other modules.  See [/FONT] 
 [FONT=arial, sans-serif]# pam-auth-update(8) for details. [/FONT] 
 

 [FONT=arial, sans-serif]# here are the per-package modules (the "Primary" block) [/FONT] 
 [FONT=arial, sans-serif]password	[success=2 default=ignore]	pam_unix.so obscure sha512 [/FONT] 
 [FONT=arial, sans-serif]password	[success=1 user_unknown=ignore default=die]	pam_ldap.so  try_first_pass [/FONT] 
 [FONT=arial, sans-serif]# here's the fallback if no module succeeds [/FONT] 
 [FONT=arial, sans-serif]password	requisite			pam_deny.so [/FONT] 
 [FONT=arial, sans-serif]# prime the stack with a positive return value if there isn't one already; [/FONT] 
 [FONT=arial, sans-serif]# this avoids us returning an error just because nothing sets a success code [/FONT] 
 [FONT=arial, sans-serif]# since the modules above will each just jump around [/FONT] 
 [FONT=arial, sans-serif]password	required			pam_permit.so [/FONT] 
 [FONT=arial, sans-serif]# and here are more per-package modules (the "Additional" block) [/FONT] 
 [FONT=arial, sans-serif]#password	optional			pam_smbpass.so nullok  use_first_pass [/FONT] 
 [FONT=arial, sans-serif]password	optional	pam_gnome_keyring.so [/FONT] 
 [FONT=arial, sans-serif]# end of pam-auth-update config[/FONT]

---

