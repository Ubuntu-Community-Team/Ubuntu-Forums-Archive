---
title: "Software source error, no available public key..."
date: 2009-11-11
forum: General Help
---

### Post by mvalenti on 2009-11-11
this error message:
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE

for this source....
[http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu)

can someone help me with the public key? Or do i even need this source?

---

### Post by drs305 on 2009-11-11
You should be able to add the key by running this command:
```

gpg --keyserver keyserver.ubuntu.com --recv-keys 247510BE && gpg --export --armor 247510BE | sudo apt-key add -

```

The alphanumerics are the last 8 characters of the error message code.


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by user333 on 2009-11-11
So you are using the update manager???? The synaptic?????

---

