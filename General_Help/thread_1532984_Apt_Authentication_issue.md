---
title: "Apt Authentication issue"
date: 2010-07-17
forum: General Help
---

### Post by CoolJohnB on 2010-07-17
I get this message when automatic update runs:

Apt Authentication issue

Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".

When I click "Run this action now"  It comes back with a whole list of items that can't be updated for various reasons

Listed here:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B152F042D246C25D
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures were invalid: BADSIG D225991A72B194E5 Launchpad Ubuntu Audio Dev team PPA
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release](http://archive.ubuntu.com/ubuntu/dists/lucid/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Some index files failed to download, they have been ignored, or old ones used instead.

Any help would be much appreciated, thanks.

---

### Post by flick on 2010-07-18
Method 1 from the following site/link worked for me :

[http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

---

### Post by CoolJohnB on 2010-07-18
Thanks for that, I tried it and it has helped most of the errors have gone, but I still get the ones with "no public key"

Anyone any further ideas or help?

---

