---
title: "Maverick, OpenLDAP bug, Likewise join failure"
date: 2010-10-22
forum: General Help
---

### Post by atworkwithjf on 2010-10-22
With the release of Maverick, a patched version of OpenLDAP, on which [Likewise Open]("http://likewiseopen.org/") relied, prevented successful Active Directory domain joins when using the version of [Likewise Open]("http://likewiseopen.org/") in the Ubuntu repository.

The [bug in OpenLDAP]("https://bugs.launchpad.net/ubuntu/+source/openldap/+bug/661547") has been located and a [fix submitted to the OpenLDAP]("https://bugs.launchpad.net/ubuntu/+source/openldap/+bug/661547") maintainers, however the issue will remain until a forthcoming update makes its way into the updates repo.

Until the update to OpenLDAP is released a patched version of OpenLDAP, which resolves the issue with [Likewise Open]("http://likewiseopen.org/"), has been posted:

    [https://launchpad.net/~ssalley/+archive/ppa/+packages]("https://launchpad.net/%7Essalley/+archive/ppa/+packages")

Most users will just need libldap-2.4-2_2.4.23-0ubuntu3.3_amd64.deb or libldap-2.4-2_2.4.23-0ubuntu3.3_i386.deb depending on their architecture.  Users should reboot after installing to make sure all processes pick up the new version.

---

