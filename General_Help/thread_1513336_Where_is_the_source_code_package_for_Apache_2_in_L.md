---
title: "Where is the source code package for Apache 2 in Lucid?"
date: 2010-06-19
forum: General Help
---

### Post by ampermc on 2010-06-19
In previous versions, the source code package was apache2-src. This package doesn't seem to exist for Lucid. What's the deal?

[http://packages.ubuntu.com/search?keywords=apache2](http://packages.ubuntu.com/search?keywords=apache2)

lists no package for Lucid...

---

### Post by cariboo on 2010-06-19
Have you created a bug?

---

### Post by gmargo on 2010-06-19
The source code package is available at [http://packages.ubuntu.com/source/lucid/apache2](http://packages.ubuntu.com/source/lucid/apache2) or through a simple "apt-get source apache2".

---

### Post by ampermc on 2010-06-19
Ahh...I was trying "apt-get install apache2-src"

---

### Post by ampermc on 2010-06-20
Had to install dpkg-dev first, but then got "public key not found"/"failed to verify signature" on apache2_2.2.14-5ubuntu8.dsc running "apt-get source apache2". Am I missing something?

Shouldn't the key come down automatically? I don't want to use code that can't be verified.

> root@slasher:~# apt-get source apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
NOTICE: 'apache2' packaging is maintained in the 'Bzr' version control system at:
[http://code.launchpad.net/ubuntu/+source/apache2](http://code.launchpad.net/ubuntu/+source/apache2)
Please use:
bzr get [http://code.launchpad.net/ubuntu/+source/apache2](http://code.launchpad.net/ubuntu/+source/apache2)
to retrieve the latest (possibly unreleased) updates to the package.
Skipping already downloaded file 'apache2_2.2.14-5ubuntu8.dsc'
Skipping already downloaded file 'apache2_2.2.14.orig.tar.gz'
Skipping already downloaded file 'apache2_2.2.14-5ubuntu8.diff.gz'
Need to get 0B of source archives.
gpgv: Signature made Tue 13 Apr 2010 03:11:50 PM EDT using DSA key ID FA14013B
gpgv: Can't check signature: public key not found
dpkg-source: warning: failed to verify signature on ./apache2_2.2.14-5ubuntu8.dsc
dpkg-source: info: extracting apache2 in apache2-2.2.14
dpkg-source: info: unpacking apache2_2.2.14.orig.tar.gz
dpkg-source: info: applying apache2_2.2.14-5ubuntu8.diff.gz


---

### Post by gmargo on 2010-06-20
Not sure this is the right way to do it, but try this:
```

gpg --keyserver keyserver.ubuntu.com --recv-keys FA14013B
gpg --export > $HOME/.gnupg/trustedkeys.gpg
 
```Now try the "apt-get source apache2" again, and it should find and verify the signature.

---

### Post by ampermc on 2010-06-21
> **gmargo said:**
> Not sure this is the right way to do it, but try this:
```

gpg --keyserver keyserver.ubuntu.com --recv-keys FA14013B
gpg --export > $HOME/.gnupg/trustedkeys.gpg
 
```Now try the "apt-get source apache2" again, and it should find and verify the signature.

Tried that, got same message about "public key not found" when re-running "apt-get source apache2".

EDIT: Never mind. I had forgotten to run the export command...

> root@slasher:~# gpg --keyserver keyserver.ubuntu.com --recv-keys FA14013B
gpg: requesting key FA14013B from hkp server keyserver.ubuntu.com
gpg: /root/.gnupg/trustdb.gpg: trustdb created
gpg: key FA14013B: public key "Chuck Short <chuck.short@canonical.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1

---

