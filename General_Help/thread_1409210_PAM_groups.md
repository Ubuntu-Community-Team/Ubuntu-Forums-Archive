---
title: "PAM groups"
date: 2010-02-17
forum: General Help
---

### Post by msp3k on 2010-02-17
Hi guys,

I'm setting up a new Ubuntu network using LDAP for authentication.  I'm trying to figure out the PAM groups thing.   (I've done this before several years ago on Debian Sarge, but for some reason the same approach on Ubuntu Karmic isn't working.)

I edit /etc/pam.d/common-auth and put:
```
auth required pam_group.so use_first_pass
```before
```
auth    [success=1 default=ignore]    pam_ldap.so use_first_pass
```Then I edit /etc/security/group.conf and put:
```
*;*;*;Al0000-2400;fax,voice,cdrom,floppy,audio,dip,video,plugdev,users,fuse,saned,vboxusers
```Not only does this not work (i.e. SSH'ing in and typing "groups" does not list me as being in any of these groups), but it actually breaks gdm logins ("Authentication failure").

Can someone clue me in?

Thanks,

Michael

---

### Post by msp3k on 2010-02-17
The line for pam_group.so needs to go at the end of /etc/pam.d/common-auth, not before the line containing pam_ldap.so.

I was following what was apparently an outdated HOWTO intended for an older version of Ubuntu, and apparently the way PAM works has changed since then.

---

