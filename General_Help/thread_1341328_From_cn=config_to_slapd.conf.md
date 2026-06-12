---
title: "From cn=config to slapd.conf"
date: 2009-11-29
forum: General Help
---

### Post by poisn on 2009-11-29
Hi all,

my problem is that I'm working with the old openLDAP (with the slapd.conf file). The tutorial I'm doing atm is working with the newer one though (with slapd.d directory). I tried searching for guides which tell you how to get from slapd.d to slapd.conf, but all I get is "convert from slapd.conf to cn=config".

Can anyone tell me how I can do this:
**ldapmodify -x -D cn=admin,cn=config -W**
in slapd.conf?

I have no clue what to use instead of cn=config.

Any help is greatly appreciated!

(Doing this tutorial: [https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html))

---

