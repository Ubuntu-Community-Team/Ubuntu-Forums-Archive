---
title: "Public Key Error"
date: 2010-05-11
forum: General Help
---

### Post by AdamMPkins on 2010-05-11
I keep getting the following error when trying to run update manager:
```
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 665F9AEFE1098513

```

I assume the source for which it desires a key is for [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) lucid main universe 

...but I have been unable to find the key. In fact, I believe that I read something on screenlets' website which said that there is no public key.

---

### Post by sisco311 on 2010-05-11
[https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)

Open a terminal and run:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E1098513
sudo apt-get update
```

---

