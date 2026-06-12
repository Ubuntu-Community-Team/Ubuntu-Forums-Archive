---
title: "Keyserver broken?"
date: 2010-03-16
forum: General Help
---

### Post by c-m on 2010-03-16
Is the ubuntu keyserver broken?

I am trying to install a package and every time i try to install the key i get a time out error.

apt-update give me

```
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 932062C9CD30EE56
```

Then if i try to install the key i get this?

```
 sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CD30EE56
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys CD30EE56
gpg: requesting key CD30EE56 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
```

Can i tell ubuntu not to bother with the key. I know the package is good and safe to install. I should be the one to judge if its ok to install not ubuntu.

---

### Post by Iowan on 2010-03-16
My keyserver [problem]("http://ubuntuforums.org/showthread.php?t=1328858") wound up being firewall setting.

---

