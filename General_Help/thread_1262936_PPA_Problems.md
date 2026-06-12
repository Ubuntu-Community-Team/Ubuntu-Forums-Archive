---
title: "PPA Problems"
date: 2009-09-10
forum: General Help
---

### Post by DoubleCross on 2009-09-10
Whenever I try to install a PPA package I get the error messages

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D739676F7613768D
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8C851674F96FD737
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

I have followed several directions to the letter ans I am still having problems. Any thing is helpful at this point.

---

### Post by Elfy on 2009-09-10
Do this for each one in a terminal

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys
```

adding the last 8 digits of each signature - so for the first add BF810CD5

The whole command would then be 

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BF810CD5
```

Once you have done all then update

```
sudo apt-get update
```

[https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)

---

