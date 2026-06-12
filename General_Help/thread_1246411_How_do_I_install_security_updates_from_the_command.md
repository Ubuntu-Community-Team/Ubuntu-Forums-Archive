---
title: "How do I install security updates from the command line?"
date: 2009-08-21
forum: General Help
---

### Post by wesg on 2009-08-21
I'm running Jaunty on an x64 server with only command line, and each time I log in with SSH I find there are > 100 security updates available. 

How do I implement these and will they overwrite my compiled applications?

---

### Post by Grannun on 2009-08-21
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by slakkie on 2009-08-21
I prefer aptitude:

Make sure you have the security repo's in your sources.list:

```

deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse

```

Also, -updates is advised btw

```

deb http://nl.archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse

```

When you've added these to your sources (change hardy to your release of course), then we do the upgrade:

```

sudo aptitude update && sudo aptitude safe-upgrade

```

Done.

---

### Post by Grannun on 2009-08-21
but since he is using jaunty, he should replace all of those "hardy" with "jaunty"

---

