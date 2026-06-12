---
title: "apt-get errors"
date: 2009-10-14
forum: General Help
---

### Post by vhenry on 2009-10-14
I'm getting some errors when I run sudo apt-get update and not sure how to correct. Any ideas?

W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F104610CF0876AC9
W: You may want to run apt-get update to correct these problems

---

### Post by KlinerDraken on 2009-10-14
when you added some PPA's you did not get the public key.

here is the one you need for Virtual Box:

```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
```

---

### Post by slakkie on 2009-10-15
This is a command you might want to remember:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <KEY_ID>

```

If I use the key of virtualbox it would be:

```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DCF9F87B6DFBCBAE
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys DCF9F87B6DFBCBAE
gpg: requesting key 6DFBCBAE from hkp server keyserver.ubuntu.com
gpg: key 6DFBCBAE: public key "Sun Microsystems, Inc. (xVM VirtualBox archive signing key) <info@virtualbox.org>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1

```

---

### Post by vhenry on 2009-10-16
Thanks! Did the trick.

---

