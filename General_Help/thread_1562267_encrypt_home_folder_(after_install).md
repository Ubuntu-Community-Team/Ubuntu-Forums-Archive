---
title: "encrypt home folder (after install)"
date: 2010-08-27
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2010-08-27
When I set up my install I chose to not encrypt my home folder.
lets say I change my mind and want to encrypt it now, how would I go about doing it?

---

### Post by pqwoerituytrueiwoq on 2010-08-31
4 days layer...

---

### Post by miesogeno on 2010-09-06
5 days later, i have the same question.

do you know the answer yet?

---

### Post by afrowildo on 2010-09-06
Does this help you any?

[https://wiki.ubuntu.com/EncryptedHomeFolder](https://wiki.ubuntu.com/EncryptedHomeFolder)

---

### Post by miesogeno on 2010-09-06
i guess it does. not sure if it is just a workaround or the real thing. i thought it would be something like ticking a box somewhere on system admin.

thank you.

---

### Post by pqwoerituytrueiwoq on 2010-09-30
> **Configure PAM**

 Insert the line  

[LIST]
[*]auth    sufficient      pam_encfs.so 
[/LIST]
Somewhere before:  

[LIST]
[*]auth    requisite       pam_unix.so  
[/LIST]
and append "use_first_pass" to each line following pam_encfs.so. 

[LIST]
[*]$ sudo gedit /etc/pam.d/common-auth 
[/LIST]
Here's my common-auth as an example: 

[LIST]
[*]auth    sufficient      pam_encfs.so 
[*]auth    requisite       pam_unix.so nullok_secure use_first_pass 
[*]auth    optional        pam_smbpass.so migrate use_first_pass
[/LIST]

one problem i have no "auth    requisite       pam_unix.so" line
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
auth    [success=2 default=ignore]    pam_unix.so nullok_secure
auth    [success=1 default=ignore]    pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login try_first_pass
# here's the fallback if no module succeeds
auth    requisite            pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required            pam_permit.so
# and here are more per-package modules (the "Additional" block)
auth    optional            pam_cap.so 
# end of pam-auth-update config
```

---

### Post by JohnElway on 2010-09-30
I use encfs to encrypt some financial documents I keep on a flash drive, but the setup process I used seems much simpler than the process detailed in the posted link. All I did was the following:

-install encfs:

```
sudo apt-get install encfs
```

-add your user account to fuse:

```
sudo adduser **yourusernamehere** fuse
```

-create two directories: one for your encrypted folder and one for your mount point folder (they must both be empty to start with)

-mount the encrypted folder to the mount point folder(on first mount it'll ask you to choose a configuration setup, I always go with the standard option):

```
encfs /path/to/encrypted/directory/ /path/to/mount/directory/
```

-add/delete files or folders to the mount point folder

-when you're done, unmount the mount point folder:

```
fusermount -u /path/to/mount/directory/
```

The obvious limitation with this setup method is that you cannot encrypt folders that already have data in them (they must be empty to start with) AFAIK, so this may not work for what you're asking. But if you don't get a workable solution, you can always use the above to create an encrypted folder within your home folder for storing all your important data.

---

