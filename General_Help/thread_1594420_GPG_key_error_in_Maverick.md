---
title: "GPG key error in Maverick"
date: 2010-10-12
forum: General Help
---

### Post by rps63ifid on 2010-10-12
I've been seeing the sort of GPG key error described above for the past 2+ days and I've tried several times to update the keys but all I ever get is a "couldn't connect, connection timed out error":

$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E871C4A881574DE 16126D3A3E5C1192
[sudo] password for ron: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 6E871C4A881574DE 16126D3A3E5C1192
gpg: requesting key 881574DE from hkp server keyserver.ubuntu.com
gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: Connection timed out
gpgkeys: HTTP fetch error 7: couldn't connect: Connection timed out
?: keyserver.ubuntu.com: Connection timed out
gpgkeys: HTTP fetch error 7: couldn't connect: Connection timed out
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

Any ideas what's wrong here? I'm not seeing any other network-related problems...

Thanks in advance?

-- 
/ron

---

