---
title: "Cached Credentials PAM and LDAP on Ubuntu 9.04"
date: 2009-09-30
forum: General Help
---

### Post by dinkoarun on 2009-09-30
I am trying to use cached credential login to my client using cached LDAP username and password. When my network is available, my client automatically authenticates against the LDAP server. I have a problem only when the network is down. I am not able to login to the client as it is not able to contact the LDAP server. 

For this reason I have decided to setup PAMCcreds following the instruction of this Howtowiki [https://help.ubuntu.com/community/PamCcredsHowto]("https://help.ubuntu.com/community/PamCcredsHowto")

But somehow I still unable to login to the client. I've edited the /etc/nsswitch.conf as per the wiki. 

Also here the configurations for **/etc/pam.d/common-auth,** 

```
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
auth	[success=2 default=ignore]	pam_unix.so nullok_secure
auth	[success=1 default=ignore]	pam_ldap.so use_first_pass
# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config
```

Here are the configurations for **/etc/pam.d/common-account**
```

# /etc/pam.d/common-account - authorization settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authorization modules that define
# the central access policy for use on the system.  The default is to
# only deny service to users whose accounts are expired in /etc/shadow.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.
#

# here are the per-package modules (the "Primary" block)
account	[success=2 new_authtok_reqd=done default=ignore]	pam_unix.so 
account	[success=1 default=ignore]	pam_ldap.so 
# here's the fallback if no module succeeds
account	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
account	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config
```


Here are the configurations for **/etc/pam.d/common-session**
```
#
# /etc/pam.d/common-session - session-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define tasks to be performed
# at the start and end of sessions of *any* kind (both interactive and
# non-interactive).
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
session	[default=1]			pam_permit.so
# here's the fallback if no module succeeds
session	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
session	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
session	required	pam_unix.so 
session required	pam_mkhomedir.so skel=/etc/skel
session	optional			pam_ldap.so 
session	optional			pam_ck_connector.so nox11
# end of pam-auth-update config
```

Arun

---

### Post by nickpiggott on 2011-01-08
I have the same problem.

I think there is a bug in common-account. The line:

```
account    [success=1 default=ignore]    pam_ldap.so
```will always fail, because if the machine is off-line, it cannot contact the LDAP server.

I have amended that line in my common-account to read:

```
account    [success=1 authinfo_unavail=1 default=ignore]    pam_ldap.so 
```If the LDAP server cannot be reached, it now proceeds as if it had succeeded.

There are some potential dangers to this approach, but it's a working solution for me.

---

