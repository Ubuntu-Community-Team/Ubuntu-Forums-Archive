---
title: "KRB5/PAM/NIS/AD SSH login works, sudo can't authenticate"
date: 2012-05-15
forum: General Help
---

### Post by Ginkel on 2012-05-15
I have run into a strange situation: users are able to login to my Ubuntu 12.04 virtual server but they are not able to use sudo, even while they are in the sudoers file.

Users are administrate in the active domain of our MS Windows 2008 environment, which doesn't have a Linux/UNIX connector. To facilitate in the login in of our users with just 1 account we use a NIS server - old server with SunOS 9 on it. On the Ubuntu server this server is configured in yp.conf, and in krb5.conf the realm configuration along with pam application settings are set.

When I SSH-logon with a local user (local account on the Ubuntu server) which is in the sudoers file, I am able to use sudo without any problems. If I sudo to root and then su to a domain account (which is also in the sudoers file), I am able to use sudo while authenticating with the domain users password.
However, if I would SSH-logon with that domain account and try to sudo, this is denied with the following error lines in the log:
```

authpriv.notice: May 15 14:39:46 sudo: pam_unix(sudo:auth): authentication failure; logname=domuser uid=11211 euid=0 tty=/dev/pts/18 ruser=domuser rhost=  user=domuser
authpriv.crit: May 15 14:39:54 sudo: pam_unix(sudo:auth): auth could not identify password for [domuser]
authpriv.alert: May 15 14:39:54 sudo: domuser : 1 incorrect password attempt ; TTY=pts/18 ; PWD=/home/domuser ; USER=root ; COMMAND=/bin/su -

```

Somehow I suspect an illconfigured pam file, but I am not able to point my finger to the error.

I'll list a few configuration files below: krb5.conf, nsswitch.conf, yp.conf and a few pam.d files.

krb5.conf
```

[libdefaults]
        default_realm = OUR.DOMAIN
        clockskew = 300

[realms]
        OUR.DOMAIN = {
                kdc = win2008server.our.domain
                default_domain = OUR.DOMAIN
                admin_server = win2008server.our.domain
        }

[domain_realm]
        .OUR.DOMAIN = OUR.DOMAIN

[appdefaults]
    pam = {
            debug = true
            ticket_lifetime = 10h
            renew_lifetime = 9h
            forwardable = true
            proxiable = false
            retain_after_close = false
            minimum_uid = 0
            try_first_pass = true
    }

[login]
        krb4_convert = true
        krb4_get_tickets = false


```

nsswitch.conf
```

passwd:         compat nis
group:          compat nis
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files dns

netgroup:       nis

services:       files dns
protocols:      files
rpc:            files
ethers:         files
netmasks:       files dns
publickey:      files

bootparams:     files
automount:      files
aliases:        files

```

yp.conf
```

domain nisdomain server 123.45.67.89

```

pam.d/common-auth
```

auth    [success=2 default=ignore]      pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login try_first_pass
auth    [success=1 default=ignore]      pam_unix.so nullok_secure
auth    requisite                       pam_deny.so
auth    required                        pam_permit.so
auth    optional                        pam_cap.so

```

pam.d/common-account
```

account [success=2 new_authtok_reqd=done default=ignore]        pam_unix.so
account [success=1 new_authtok_reqd=done default=ignore]        pam_winbind.so
account requisite                       pam_deny.so
account required                        pam_permit.so

```

pam.d/sudo
```

#%PAM-1.0

@include common-auth
@include common-account
@include common-session-noninteractive

```

---

### Post by Ginkel on 2012-05-22
Is there anyone who can shed some light on my problem? I am suspecting pam settings - perhaps in combination with winbind, but I have no idea what to modify to solve this problem.

---

### Post by roelforg on 2012-05-22
Whats the error that sudo outputs?
Good chance it has something to do with the sudoers file.

---

### Post by Ginkel on 2012-05-22
Error snip:
```

authpriv.notice: May 22 07:57:38 sudo: pam_unix(sudo:auth): authentication failure; logname=localadmin uid=12345 euid=0 tty=/dev/pts/15 ruser=abc12345 rhost=  user=abc12345
authpriv.crit: May 22 07:58:04 sudo: pam_unix(sudo:auth): auth could not identify password for [abc12345]
authpriv.alert: May 22 07:58:04 sudo: abc12345 : 2 incorrect password attempts ; TTY=pts/15 ; PWD=/home/abc12345 ; USER=root ; COMMAND=/usr/bin/apt-get install htop

```


Sudoers file:
```

Defaults        env_reset

# User privilege specification
root            ALL=(ALL) ALL
localadmin      ALL=(ALL) ALL

# Sudoers for maintaining
abc12345        ALL=(ALL) ALL

%admin ALL=(ALL) ALL

%group1 ALL=NOPASSWD: /bin/mount
%group1 ALL=NOPASSWD: /bin/umount
%group1 ALL=NOPASSWD: /usr/bin/smbpasswd

user ALL=NOPASSWD: /bin/mount
user ALL=NOPASSWD: /bin/umount
user ALL=NOPASSWD: /usr/bin/smbpasswd

```

When I use the local account localadmin sudo works fine, but the AD user abc12345 gives the error message above. I've ruled out a password entry error by key logging my entry.

---

### Post by roelforg on 2012-05-22
> **Ginkel said:**
> Error snip:
```

authpriv.notice: May 22 07:57:38 sudo: pam_unix(sudo:auth): authentication failure; logname=localadmin uid=12345 euid=0 tty=/dev/pts/15 ruser=abc12345 rhost=  user=abc12345
authpriv.crit: May 22 07:58:04 sudo: pam_unix(sudo:auth): auth could not identify password for [abc12345]
authpriv.alert: May 22 07:58:04 sudo: abc12345 : 2 incorrect password attempts ; TTY=pts/15 ; PWD=/home/abc12345 ; USER=root ; COMMAND=/usr/bin/apt-get install htop

```
 
 
Sudoers file:
```

Defaults        env_reset
 
# User privilege specification
root            ALL=(ALL) ALL
localadmin      ALL=(ALL) ALL
 
# Sudoers for maintaining
abc12345        ALL=(ALL) ALL
 
%admin ALL=(ALL) ALL
 
%group1 ALL=NOPASSWD: /bin/mount
%group1 ALL=NOPASSWD: /bin/umount
%group1 ALL=NOPASSWD: /usr/bin/smbpasswd
 
user ALL=NOPASSWD: /bin/mount
user ALL=NOPASSWD: /bin/umount
user ALL=NOPASSWD: /usr/bin/smbpasswd

```
 
When I use the local account localadmin sudo works fine, but the AD user abc12345 gives the error message above. I've ruled out a password entry error by key logging my entry.
 
Don't you need to be in either the admin or the sudo group (can't remember which one) to use sudo?

---

### Post by Ginkel on 2012-05-22
> **roelforg said:**
> Don't you need to be in either the admin or the sudo group (can't remember which one) to use sudo?

No, that is not needed.

---

### Post by roelforg on 2012-05-22
> **Ginkel said:**
> No, that is not needed.
 
Then why does it say so right there in the manual?
[https://help.ubuntu.com/community/RootSudo#Allowing_other_users_to_run_sudo](https://help.ubuntu.com/community/RootSudo#Allowing_other_users_to_run_sudo)

---

### Post by Ginkel on 2012-05-22
That manual uses %admin, you add users to the group admin, and that is called in the sudoers file. You can however add your own groups and users to the sudoers file.

---

### Post by roelforg on 2012-05-22
> **Ginkel said:**
> That manual uses %admin, you add users to the group admin, and that is called in the sudoers file. You can however add your own groups and users to the sudoers file.
 
I know that, but as it's in the manual, maybe some thing is set in his NIS setup to hardcode the admin group.
It's worth a try.

---

