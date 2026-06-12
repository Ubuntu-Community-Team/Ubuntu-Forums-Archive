---
title: "Ubuntu's sudo and su doesn't ask for password"
date: 2010-07-06
forum: General Help
---

### Post by Karapuz on 2010-07-06
Since some time ago Ubuntu doesn't ask password for sudo and su. Also if try to execute "sudo passwd" or "passwd username" it doesn't require a password.

> 
I changed /etc/sudoers and added timestamp_timeout=0 but It didn't help.

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

&#1062;&#1080;&#1090;&#1072;&#1090;&#1072;:
#Defaults	env_reset
Defaults:ALL timestamp_timeout=0

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


Also 'sudo -K' didn't help. If create new user and add it to group admin it doesn't require password.

if sudo is forbidden for user I get a message but su execute without problem.

I tried to remove /var/run/sudo/username, tried to reboot computer, but it didn't help. 

What can i do more for repair my system?

---

### Post by sisco311 on 2010-07-06
Hi and welcome to the forums!

Did you change the pam settings? Please post the content of /etc/pam.d/common-auth, /etc/pam.d/su and /etc/pam.d/sudo.

---

### Post by Karapuz on 2010-07-06
Hi, sisco311.

I didn't change this files. 

/etc/pam.d/common-auth
> #
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
auth	[default=1]			pam_permit.so
# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config

/etc/pam.d/su 
> 
#
# The PAM configuration file for the Shadow `su' service
#

# This allows root to su without passwords (normal operation)
auth       sufficient pam_rootok.so

# Uncomment this to force users to be a member of group root
# before they can use `su'. You can also add "group=foo"
# to the end of this line if you want to use a group other
# than the default "root" (but this may have side effect of
# denying "root" user, unless she's a member of "foo" or explicitly
# permitted earlier by e.g. "sufficient pam_rootok.so").
# (Replaces the `SU_WHEEL_ONLY' option from login.defs)
# auth       required   pam_wheel.so

# Uncomment this if you want wheel members to be able to
# su without a password.
# auth       sufficient pam_wheel.so trust

# Uncomment this if you want members of a specific group to not
# be allowed to use su at all.
# auth       required   pam_wheel.so deny group=nosu

# Uncomment and edit /etc/security/time.conf if you need to set
# time restrainst on su usage.
# (Replaces the `PORTTIME_CHECKS_ENAB' option from login.defs
# as well as /etc/porttime)
# account    requisite  pam_time.so

# This module parses environment configuration file(s)
# and also allows you to use an extended config
# file /etc/security/pam_env.conf.
# 
# parsing /etc/environment needs "readenv=1"
session       required   pam_env.so readenv=1
# locale variables are also kept into /etc/default/locale in etch
# reading this file *in addition to /etc/environment* does not hurt
session       required   pam_env.so readenv=1 envfile=/etc/default/locale

# Defines the MAIL environment variable
# However, userdel also needs MAIL_DIR and MAIL_FILE variables
# in /etc/login.defs to make sure that removing a user 
# also removes the user's mail spool file.
# See comments in /etc/login.defs
#
# "nopen" stands to avoid reporting new mail when su'ing to another user
session    optional   pam_mail.so nopen

# Sets up user limits, please uncomment and read /etc/security/limits.conf
# to enable this functionality.
# (Replaces the use of /etc/limits in old login)
# session    required   pam_limits.so

# The standard Unix authentication modules, used with
# NIS (man nsswitch) as well as normal /etc/passwd and
# /etc/shadow entries.
@include common-auth
@include common-account
@include common-session


/etc/pam.d/sudo
> #%PAM-1.0

@include common-auth
@include common-account

session required pam_permit.so
session required pam_limits.so


---

### Post by sisco311 on 2010-07-06
```
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.). The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules. See
# pam-auth-update( for details.

# here are the per-package modules (the "Primary" block)
**auth [default=1] pam_permit.so**
# here's the fallback if no module succeeds
auth requisite pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth required pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config
```
The bold line is the cause of the problem. It should look like this:
```
auth    [success=1 default=ignore]      pam_unix.so nullok_secure
```

Start a root shell:
```
sudo -i
```
rename the file:
```
mv /etc/pam.d/common-auth{,-bad}
```
create a new one with the default settings:
```
pam-auth-update --force
```
if a new file is created with the default settings, then logou from the root shell:
```
exit
```

---

### Post by Karapuz on 2010-07-06
Yahoooo! Thanx a lot! 

```

 pam-auth-update --force

```

doesn't help (new one created with a wrong line ), but when i changed the file manually and save everything was ok!

---

### Post by sisco311 on 2010-07-06
> **Karapuz said:**
> Yahoooo! Thanx a lot! 


You are welcome!

> **Karapuz said:**
> 
```

 pam-auth-update --force

```

doesn't help (new one created with a wrong line ), but when i changed the file manually and save everything was ok!

Hmmm, this is serious security flaw. Which version of Ubuntu are you using and what's the version number of libpam-runtime?
```
lsb_release -a
```
```
apt-cache show libpam-runtime
```

---

### Post by Karapuz on 2010-07-06
.> roman@sunion:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04 LTS
Release:	10.04
Codename:	lucid
roman@sunion:~$ apt-cache show libpam-runtime
Package: libpam-runtime
Priority: required
Section: admin
Installed-Size: 1248
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Steve Langasek <vorlon@debian.org>
Architecture: all
Source: pam
Version: 1.1.1-2ubuntu2
Replaces: libpam0g-dev, libpam0g-util
Depends: debconf (>= 1.5.19), libpam-modules (>= 1.0.1-6)
Conflicts: libpam0g-util
Filename: pool/main/p/pam/libpam-runtime_1.1.1-2ubuntu2_all.deb
Size: 114600
MD5sum: f01a410695cd57811b2e410752f13c44
SHA1: cab75fbff4883639e6ed0c8765ef54a96abcadeb
SHA256: 298f869401fd797d6be4f25075d535840287c52b3e4d827ab5244afd59227572
Description-ru: &#1087;&#1086;&#1076;&#1076;&#1077;&#1088;&#1078;&#1082;&#1072; &#1088;&#1072;&#1073;&#1086;&#1090;&#1099; &#1073;&#1080;&#1073;&#1083;&#1080;&#1086;&#1090;&#1077;&#1082;&#1080; PAM
 &#1057;&#1086;&#1076;&#1077;&#1088;&#1078;&#1080;&#1090; &#1092;&#1072;&#1081;&#1083;&#1099; &#1085;&#1072;&#1089;&#1090;&#1088;&#1086;&#1081;&#1082;&#1080; &#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1080;, &#1090;&#1088;&#1077;&#1073;&#1091;&#1102;&#1097;&#1080;&#1077;&#1089;&#1103; &#1076;&#1083;&#1103; &#1080;&#1076;&#1077;&#1085;&#1090;&#1080;&#1092;&#1080;&#1082;&#1072;&#1094;&#1080;&#1080; &#1074;
 &#1089;&#1080;&#1089;&#1090;&#1077;&#1084;&#1072;&#1093; &#1089; Debian. &#1069;&#1090;&#1086;&#1090; &#1087;&#1072;&#1082;&#1077;&#1090; &#1090;&#1088;&#1077;&#1073;&#1091;&#1077;&#1090;&#1089;&#1103; &#1087;&#1086;&#1095;&#1090;&#1080; &#1087;&#1088;&#1080; &#1082;&#1072;&#1078;&#1076;&#1086;&#1081; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1082;&#1077;
 &#1076;&#1080;&#1089;&#1090;&#1088;&#1080;&#1073;&#1091;&#1090;&#1080;&#1074;&#1072;.
Homepage: [http://pam.sourceforge.net/](http://pam.sourceforge.net/)
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 5y
Task: minimal

I use the getdeb repo, maybe this is cause of this problem?

---

### Post by sisco311 on 2010-07-06
> **Karapuz said:**
> .

I use the getdeb repo, maybe this is cause of this problem?

I don't know. I downloaded the  libpam-runtime package from the repos and it looks okay, it has the same sd5sum as yours.

Please post the content of the /usr/share/pam-configs/unix file.

---

### Post by Karapuz on 2010-07-06
.

> Name: Unix authentication
Default: yes
Priority: 256
Auth-Type: Primary
Auth:
	[success=end default=ignore]	pam_unix.so nullok_secure try_first_pass
Auth-Initial:
	[success=end default=ignore]	pam_unix.so nullok_secure
Account-Type: Primary
Account:
	[success=end new_authtok_reqd=done default=ignore]	pam_unix.so
Account-Initial:
	[success=end new_authtok_reqd=done default=ignore]	pam_unix.so
Session-Type: Additional
Session:
	required	pam_unix.so
Session-Initial:
	required	pam_unix.so
Password-Type: Primary
Password:
	[success=end default=ignore]	pam_unix.so obscure use_authtok try_first_pass sha512
Password-Initial:
	[success=end default=ignore]	pam_unix.so obscure sha512

---

### Post by sisco311 on 2010-07-06
I'm not sure what caused the problem, but everything looks good now.

---

### Post by Karapuz on 2010-07-06
When i try to execute "pam-auth-update --force" i see /etc/pam.d/common-auth has the problem again. I changed back the line again.

Ok, maybe in future I'll can understand a problem came where from. :)

---

### Post by sisco311 on 2010-07-06
> **Karapuz said:**
> When i try to execute "pam-auth-update --force" i see /etc/pam.d/common-auth has the problem again. I changed back the line again.

Ok, maybe in future I'll can understand a problem came where from. :)

Sorry, I can't figure out what is overwriting the common-auth with the wrong settings. Perhaps you should start a new thread in the Security sub-forum, hopefully someone more experienced with pam can help you.

---

### Post by Karapuz on 2010-07-08
The last update repaired the system, it works as expected. The file generates with correct line.

---

