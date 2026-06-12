---
title: "Offline LDAP Client cannot login with cached credentials"
date: 2011-03-17
forum: General Help
---

### Post by tarekeldeeb on 2011-03-17
Hello all,

I have an LDAP server holding user/pass/group for many users. Due to network issues, the server sometimes is unreachable and clients cannot login, current sessions usually freeze after a while. All client have ubuntu 10.04.2 x64.

I have went through the [outdated howto]("https://help.ubuntu.com/community/PamCcredsHowto") to cache the LDAP credentials.

I setup the 
[LIST]
[*]required packages
[*]daily cron "nss_updatedb ldap"
[*]and edited '/etc/nsswitch.conf' to have "files ldap [NOTFOUND=return] db" for both passwd and group.
[/LIST]

Currently, when I type
```
ifdown eth0
sudo getent passwd
```

I get the complete list of users correctly as if I was online. Moreover, the command "cc_dump" lists the cached credentials.

During offline, when I try to 
```
ssh <user_cached_from_cc_dump>@localhost
```
It asks for the password, I enter it, It types Ubuntu Welcome message and links to the documentation as if it will finally give me the prompt, but it freezes without login.

The outdated howto gave some instructions to edit "/etc/pam.d/common-auth" for older ubuntu versions for local passwords. I do not know the proper setting for 10.04.2.

Currently, my "/etc/pam.d/common-auth" looks like:
```
auth	[success=3 default=ignore]	pam_unix.so nullok_secure
auth	[success=2 default=ignore]	pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login try_first_pass
auth	[success=1 default=ignore]	pam_ldap.so use_first_pass
# here's the fallback if no module succeeds
 auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
 auth	required			pam_permit.so
```

and my "/etc/pam.d/common-account" looks like:
```
# here are the per-package modules (the "Primary" block)
account	[success=3 new_authtok_reqd=done default=ignore]	pam_unix.so 
account	[success=2 new_authtok_reqd=done default=ignore]	pam_winbind.so 
account	[success=1 authinfo_unavail=1 default=ignore]	pam_ldap.so 
# here's the fallback if no module succeeds
account	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
account	required			pam_permit.so
```

Did any one gone through this? Any clue?

Thanks in advance,
Tarek

---

### Post by vargax on 2011-05-18
Hi, this is my setup:

```

aptitude -y install libnss-ldap nscd nss-updatedb libnss-db libpam-ccreds

```

/etc/pam.d/common-account
```

#
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
account	[success=1 authinfo_unavail=1 default=ignore]	pam_ldap.so 
# here's the fallback if no module succeeds
account	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
account	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config

```
/etc/pam.d/common-auth
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
auth	[success=4 default=ignore]			pam_unix.so nullok_secure
auth	[success=1 authinfo_unavail=ignore default=2]	pam_ldap.so use_first_pass
auth	[success=2 default=1]				pam_ccreds.so action=validate use_first_pass
auth	[default=1]					pam_ccreds.so action=store
auth	requisite			pam_deny.so
auth	required			pam_permit.so

```
/etc/pam.d/common-session
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

# here are the per-package modules (the \"Primary\" block)
session	[default=1]			pam_permit.so
# here's the fallback if no module succeeds
session	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
session	required			pam_permit.so
# and here are more per-package modules (the \"Additional\" block)
session	required	pam_unix.so 
session required	pam_mkhomedir.so skel=/etc/skel/
session	optional	pam_ldap.so 
# end of pam-auth-update config

```
/etc/nsswitch.conf
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat ldap [NOTFOUND=return] db
group:          compat ldap [NOTFOUND=return] db
shadow:         compat ldap

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```
/etc/cron.hourly/nssupdate.sh
```

#!/bin/sh
nss_updatedb ldap
exit 0

```
```

chmod +x /etc/cron.hourly/nssupdate.sh

```

---

### Post by tarekeldeeb on 2011-05-19
Great, it worked perfectly!

After months .. you saved me!

---

