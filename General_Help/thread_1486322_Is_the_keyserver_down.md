---
title: "Is the keyserver down?"
date: 2010-05-17
forum: General Help
---

### Post by hroitblat on 2010-05-17
Is the keyserver down?
apt-add-repository ppa:psusi/ppa

It worked yesterday and this morning, but not now.

gpg: requesting key B8D488BC from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

I'm prettty sure that I am not blocking any ports.  I'm trying to install 10.04

Thanks,
Herb

---

### Post by hroitblat on 2010-05-17
It seems OK now.

---

### Post by bb002 on 2010-05-17
It doesn't seem to be down so much as excruciatingly slow.

---

### Post by MikeFlint on 2010-09-09
And again today!

It seems to pause for long long periods and then work fine again.

There must be something in the route to the keyserver???

Has anyone tried just going for the keyserver IP address, or adding a specific route to it?  Maybe that would help.

---

### Post by MikeFlint on 2010-09-09
Can that ... the route to the server is fine.  It's the server itself that doesn't want to answer.

Maybe it's doing lots of key serving?!

---

