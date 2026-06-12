---
title: "What on Earth does this mean?"
date: 2012-02-18
forum: General Help
---

### Post by DarkReaperZer0 on 2012-02-18
W:GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192, W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 187206A44933B6AB, W:GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>, W:Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/dists/oneiric/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by 3rdalbum on 2012-02-19
The first set of messages says "I don't have the authentication key for this repository, so I can't check that the repository hasn't been tampered with. But I can still install software from here. To be safer, you should add its authentication key."

The second message is just referring to the Ubuntu CD. Don't worry about it.

---

### Post by plucky on 2012-02-19
> W:Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/dists/oneiric/restricted/binary-i386/Packages Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

You could open "Software Sources" and un-tick the CDrom as a source.That will get rid of the above message.

Good Luck

---

### Post by JOHNNYG713 on 2012-02-19
For the missing keys see this [https://www.ultimateeditionoz.com/forum/viewtopic.php?f=23&t=15http://](https://www.ultimateeditionoz.com/forum/viewtopic.php?f=23&t=15http://)

---

### Post by oldos2er on 2012-02-19
Fix the NO_PUBKEY errors with ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
``` where KEYID is the alphanumeric string given in the error msg.

---

