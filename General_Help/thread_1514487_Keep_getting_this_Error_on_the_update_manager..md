---
title: "Keep getting this Error on the update manager."
date: 2010-06-21
forum: General Help
---

### Post by mranima on 2010-06-21
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 991E6CF92D9A3C5B

This error keeps coming every time a new update is available or me checking for them.It just keeps popping up.

---

### Post by germanix on 2010-06-21
I had the same problem . Only my problem was with the medibuntu public key. The following command in the terminal solved my problem:

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

You could try this but exchange the medibuntu-keyring for the launchpad public key. I am however not sure what you need to enter for the launchpad key.

sudo apt-get update

 alone may also help

---

### Post by plucky on 2010-06-21
> **mranima said:**
> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 991E6CF92D9A3C5B

This error keeps coming every time a new update is available or me checking for them.It just keeps popping up.

Your link points to the PPA index file and not to an actual PPA.
Can you please post the output from a terminal of ```
cat /etc/apt/sources.list
ls -l etc/apt/sources.list.d
```

Good Luck

---

