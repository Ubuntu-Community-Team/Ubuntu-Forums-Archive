---
title: "LDAP + Cached Credentials - primary group only"
date: 2011-03-16
forum: General Help
---

### Post by the_original_billq on 2011-03-16
My ubuntu 10.10 workstation build using cached credentials to LDAP works fine in most respects, but seems to only provide primary group membership.  On our RHEL servers that are authenticating to the same LDAP back-end, but without the cached credentials, the group membership is correct.

In LDAP, I am a member of the groups: admins, users, and developers.  My primary group is admins.  My user id is billq.

On my Ubuntu workstation, when I do "groups billq", the only thing that returns is admins.  On the RHEL server (without cached creds), I do "groups billq" and it returns "admins users developers".

Here's what I believe is the relevant portion of my sssd.conf:

[domain/LDAP]
id_provider = ldap
auth_provider = ldap
ldap_schema = rfc2307
ldap_uri = ldaps://ldap.example.com
ldap_search_base = o=example
ldap_tls_reqcert = allow
cache_credentials = true
enumerate = true

I appreciate any pointers.  Thanks in advance.

-Bill

---

### Post by the_original_billq on 2011-03-27
Bump.

Nobody?  Not even a thought?  If this doesn't work, we'll roll out 3000 RHEL workstations instead of Ubuntu.  This is core functionality, folks, and you mean to say *nobody else* is affected?

---

### Post by druhboruch on 2011-04-30
You may try to add the following to /etc/security/group.conf

```
gdm;*;*;Al0000-9000;adm,cdrom,floppy,tape,audio,dip,video,plugdev,fuse,lpadmin,admin,netdev,kvm,libvirtd

```

or any other group you require.

---

