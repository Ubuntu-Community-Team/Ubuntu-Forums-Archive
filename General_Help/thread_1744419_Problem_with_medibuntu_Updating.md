---
title: "Problem with medibuntu Updating"
date: 2011-04-30
forum: General Help
---

### Post by amissot on 2011-04-30
When I try and update

```
sudo apt-get update
```

I get

```
 W: GPG error: http://packages.medibuntu.org natty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/natty-getdeb/Release  Unable to find expected entry 'game/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I have natty 11.04

and a laptop with 4GB ram and i5 processor

What should I do?

Thanks Andy

---

### Post by amissot on 2011-04-30
Hi i'm quite inexperienced in the forum but have been using Ubuntu for around a year.

When I try and update

```
sudo apt-get update
```

I get

```
W: GPG error: http://packages.medibuntu.org natty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/natty-getdeb/Release  Unable to find expected entry 'game/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

```

I have disabled them in software sources and then it's fine but I would rather have these two repositories.

Any help would be much appreciated

Andy

---

### Post by amissot on 2011-04-30
This is a very annoying error as I cannot install anything from getdeb and the applications don't appear in the software cantre.

cheers

---

### Post by oldos2er on 2011-04-30
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
```

---

### Post by idkpmiller on 2012-05-05
Thanks oldos2er your solution worked a treat for me.

---

### Post by oldos2er on 2012-05-06
You're welcome; and with that this thread is closed.

---

