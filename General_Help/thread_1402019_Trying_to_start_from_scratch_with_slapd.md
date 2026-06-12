---
title: "Trying to start from scratch with slapd"
date: 2010-02-08
forum: General Help
---

### Post by effigies on 2010-02-08
I had slapd installed, and, to a certain extent, the ldap database populated. When connecting to it with ldapsoft's admin tool, it caused it say it couldn't read the schema.

Seeing that there existed this tutorial:

[https://help.ubuntu.com/9.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/9.10/serverguide/C/openldap-server.html)

I figured I'd scrap what I had and start from scratch.

So I apt-get removed slapd, deleted its configuration files, and reinstalled.

And it did not repopulate the configuration files. It doesn't matter if I open up the deb package and manually put the config files back, things refuse to work as described in that tutorial.

I'm sick to death of playing with this. I just want to start from scratch, and have things work as expected. Does anybody know how to do this?

Thanks.

---

