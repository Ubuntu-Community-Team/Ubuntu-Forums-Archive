---
title: "Help with apt-get"
date: 2012-03-17
forum: General Help
---

### Post by jamescyan on 2012-03-17
When I tried to install a package using apt-get, I got the "Invalid Argument" errors. Could anybody help me with that? Thanks

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  postfix-cdb postfix-ldap postfix-mysql postfix-pcre postfix-pgsql procmail resolvconf
  sasl2-bin
The following packages will be REMOVED:
  exim4 exim4-base exim4-config exim4-daemon-light
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 4 to remove and 80 not upgraded.
Need to get 0B/1230kB of archives.
After this operation, 778kB disk space will be freed.
Do you want to continue [Y/n]? y
E: Could not open file /tmp/postfix.template.29600 - open (22 Invalid argument)
E: Unable to write to /tmp/postfix.template.29600 - ofstream::ofstream (22 Invalid argument)
E: Could not open file /tmp/postfix.config.29601 - open (22 Invalid argument)
E: Unable to write to /tmp/postfix.config.29601 - ofstream::ofstream (22 Invalid argument)
debconf: apt-extracttemplates failed: Bad file descriptor
dpkg: unable to create `/var/lib/dpkg/updates/tmp.i': Invalid argument
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by nauyuhs on 2012-03-17
I've also met such problem. even I used scp to transmit file to the server, it reports invalid arguments

---

### Post by Helen McCall on 2012-03-17
Are you installing from the Ubuntu repositories? Or are you installing from a ppa?

This looks like you are installing a broken package.

Which version of Ubuntu are you using?

---

