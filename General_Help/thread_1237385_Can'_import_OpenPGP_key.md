---
title: "Can' import OpenPGP key"
date: 2009-08-11
forum: General Help
---

### Post by TuckLive on 2009-08-11
I'm trying to import my OpenPGP key to sign the code of conduct on Launchpad, but I'm getting this error.  I pinged the server and was able to hit it.  What can I do?

```

gpg --send-keys --keyserver keyserver.ubuntu.com

gpgkeys: HTTP post error 7: couldn't connect to host
gpg: keyserver internal error
gpg: keyserver send failed: keyserver error
```

---

### Post by arky on 2009-08-11
Perhaps you have network problems?

---

### Post by michy99 on 2009-08-11
The server could be down.

---

### Post by TuckLive on 2009-08-11
I'm getting a failed to connect on FF when I try [http://keyserver.ubuntu.com:11371](http://keyserver.ubuntu.com:11371)

UPDATE:  Firewall problems.  I had to open up port 11371.  Hard to solve a problem when your firewall isn't showing what it's blocking :(

---

