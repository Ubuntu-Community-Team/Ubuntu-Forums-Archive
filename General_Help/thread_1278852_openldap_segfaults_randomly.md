---
title: "openldap segfaults randomly"
date: 2009-09-30
forum: General Help
---

### Post by flipybcn on 2009-09-30
Hi,
I've a server with OpenLDAP setted up, and it has been working for the last two month without any problem.

Two days ago it started to segfault randomly, every 60 to 90 min aprox.
Taking a look at the logs I cannot see anything that gives me a hint about what is happening.
I've had to set up a cron job to start slapd every 30 min, just to keep it working.
I don't think it's related to a hardware failure, since it's inside a VM server and the other servers didn't had any trouble.

The error is:
Sep 29 18:03:49 earth kernel: [ 3460.052677] slapd[2522]: segfault at 0 ip 00007f20f0285ee6 sp 00007f20eab933d8 error 4 in libc-2.9.so[7f20f0205000+168000]

Package information:
Package: slapd
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 4176
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: openldap
Version: 2.4.15-1ubuntu3
Replaces: apparmor-profiles (<< 2.1+1075-0ubuntu4), ldap-utils (<< 2.2.23-3), libldap2
Provides: ldap-server, libslapi-2.4-2
Depends: libc6 (>= 2.4), libdb4.7, libgcrypt11 (>= 1.4.0), libgnutls26 (>= 2.4.0-0), libldap-2.4-2 (= 2.4.15-1ubuntu3), libltdl7 (>= 2.2.6a), libperl5.10 (>= 5.10.0), libsasl2-2, libslp1, libtasn1-3 (>= 0.3.4), libwrap0 (>= 7.6-4~), unixodbc (>= 2.2.11-1), zlib1g (>= 1:1.1.4), coreutils (>= 4.5.1-1), psmisc, perl (>> 5.8.0) | libmime-base64-perl, adduser
Pre-Depends: debconf (>= 0.5) | debconf-2.0
Recommends: libsasl2-modules, apparmor (>= 2.1+1075-0ubuntu6)
Suggests: ldap-utils
Conflicts: apparmor-profiles (<< 2.1+1075-0ubuntu4), ldap-server, libltdl3 (= 1.5.4-1), umich-ldapd
Conffiles:
 /etc/ldap/schema/README 75d47a3e08b97dffa8635e5550fb73fa
 /etc/ldap/schema/core.ldif 696de610fca8939b10392ac1b658b935
 /etc/ldap/schema/cosine.ldif 87b6875bab54b0834007587d8e229471
 /etc/ldap/schema/inetorgperson.ldif 6ad11e84027b40a143f6fad5ac7fb5a4
 /etc/ldap/schema/misc.ldif 362c0a6a819610afcea3edf7870f7dfa
 /etc/ldap/schema/nis.ldif 834246132413c223064196be3e777cc1
 /etc/ldap/schema/openldap.ldif e53a7b15a2614ae3f9d38af993a75528
 /etc/ldap/schema/collective.schema 45f564d16366940edf19a8ab5b438a00
 /etc/ldap/schema/corba.schema 2b64119f0e3f6bf8f2a70071f6b1303a
 /etc/ldap/schema/core.schema ee6554daab76de7a92d05242c8d935e2
 /etc/ldap/schema/cosine.schema 31b5e0777b68a1c412ecbdb3e746f733
 /etc/ldap/schema/duaconf.schema 7eeff72d1a481d3d56ff1a6bf7df1717
 /etc/ldap/schema/dyngroup.schema 819b16592a2e9777d4dcad22a91f3fad
 /etc/ldap/schema/inetorgperson.schema 6b16212ebff7b2dcfbb006760cd5b990
 /etc/ldap/schema/java.schema 356dd286f40473e52d46151eaf31be65
 /etc/ldap/schema/misc.schema f4d5eb510770593d4ec62fb90c3f5ccf
 /etc/ldap/schema/nadf.schema d6765e5f63cd7226e6c74cbf7200fd62
 /etc/ldap/schema/nis.schema fd51ec5a74d83d08c5b16f8db4f43cc2
 /etc/ldap/schema/openldap.schema 8da2b265cb1405fd373c97c61010de40
 /etc/ldap/schema/pmi.schema e2e966ce44a23e08f1d001c9f520309c
 /etc/ldap/schema/ppolicy.schema c1b0752b583f71aa2d536888cf1716ee
 /etc/apparmor.d/usr.sbin.slapd df3b272d3d7a2715632412d4379c55a7
 /etc/default/slapd 785b3f25ccea0ad851e803d67a65fe3e
 /etc/init.d/slapd 7b0e0cc255e58365e7e7da0dd0244d33
Description: OpenLDAP server (slapd)
 This is the OpenLDAP (Lightweight Directory Access Protocol) server
 (slapd). The server can be used to provide a standalone directory
 service.
Homepage: [http://www.openldap.org/](http://www.openldap.org/)
Original-Maintainer: Debian OpenLDAP Maintainers <pkg-openldap-devel@lists.alioth.debian.org>

Any hint?

Thanks.

Regards,
Andreas Calvo

---

