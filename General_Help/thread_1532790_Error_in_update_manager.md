---
title: "Error in update manager"
date: 2010-07-16
forum: General Help
---

### Post by rabear on 2010-07-16
I have Ubuntu 10.04 and all of a sudden I get an error when I try to manually run the update manager.

The Error is:

GPG error: [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

Any body have an idea how to solve?

---

### Post by marshmallow1304 on 2010-07-16
System->Administration->Software Sources

On the Ubuntu Software tab, uncheck the CD-ROM (at the bottom).

---

### Post by rabear on 2010-07-17
Thank you. That solved a lot of the problem. 

I am just left with this part:

W: GPG error: [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29
 

Any ideas on this part?

Thanks,

---

### Post by CoolJohnB on 2010-07-18
I have the same error plus:
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B152F042D246C25D
W: Failed to fetch [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release.gpg](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release.gpg)  Something wicked happened resolving 'downloads.sourceforge.net:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/gutsy/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/gutsy/non-free/i18n/Translation-en_US.bz2)  Error reading from server. Remote end closed connection

W: Failed to fetch [http://archive.ubuntu.uasw.edu/dists/lucid/universe/source/Sources.bz2](http://archive.ubuntu.uasw.edu/dists/lucid/universe/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.
Any help would be appreciated.

---

### Post by philinux on 2010-07-18
> **rabear said:**
> Thank you. That solved a lot of the problem. 

I am just left with this part:

W: GPG error: [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29
 

Any ideas on this part?

Thanks,

[http://ubuntuforums.org/showthread.php?t=1221323](http://ubuntuforums.org/showthread.php?t=1221323)

---

### Post by CoolJohnB on 2010-07-18
> **philinux said:**
> [http://ubuntuforums.org/showthread.php?t=1221323](http://ubuntuforums.org/showthread.php?t=1221323)

Thanks thats fixed the public key errors I now have these left:

W: Failed to fetch [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release.gpg](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release.gpg)  Something wicked happened resolving 'downloads.sourceforge.net:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/gutsy/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/gutsy/non-free/i18n/Translation-en_US.bz2)  Error reading from server. Remote end closed connection

W: Failed to fetch [http://archive.ubuntu.uasw.edu/dists/lucid/universe/source/Sources.bz2](http://archive.ubuntu.uasw.edu/dists/lucid/universe/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

 Any further suggestions?

---

### Post by rabear on 2010-07-18
That worked great for me. My problem is solved. Thank you very much.

---

