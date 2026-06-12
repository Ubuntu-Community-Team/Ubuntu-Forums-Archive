---
title: "software sources fails when trying to check"
date: 2009-08-01
forum: General Help
---

### Post by nacho32 on 2009-08-01
I get this error any ideas ?


W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E494DBB2F021AC1
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A6DCF7707EBC211F

---

### Post by michy99 on 2009-08-01
Run these commands in a terminal:```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2F021AC1
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7EBC211F
sudo apt-get update
```

---

### Post by nacho32 on 2009-08-01
that worked like a charm thanks:D

---

### Post by nacho32 on 2009-08-01
the only problem is my cario dock fails hopefully it's just the server is down
[Connecting to repository.cairo-dock.org (87.98.128.158)]

---

### Post by kweinert on 2009-08-07
Thanks from me as well - worked like a charm here.

Thanks again.

---

### Post by lordgreg on 2009-10-05
> **michy99 said:**
> Run these commands in a terminal:```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2F021AC1
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7EBC211F
sudo apt-get update
```

sorry to bring this topic to current date again, but i'm having exactly the same GPG errors. the thing is, updating keys does not work:

```
gregor@Warlock:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2F021AC1
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 2F021AC1
gpg: requesting key 2F021AC1 from hkp server keyserver.ubuntu.com
gpgkeys: key 2F021AC1 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
```

same goes with 2nd key.

any help?

thank you,

-gregor

---

