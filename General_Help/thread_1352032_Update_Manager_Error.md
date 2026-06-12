---
title: "Update Manager Error"
date: 2009-12-11
forum: General Help
---

### Post by schlep3 on 2009-12-11
So I started up the update manager and got error message:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89


I have no idea what's going on. I tried to remove it from the source list hoping that might fix it, but it didn't work.

Any ideas?

---

### Post by MelDJ on 2009-12-11
try the link in my sig

---

### Post by schlep3 on 2009-12-11
Yeah, I saw that when I was checking out Google for a fix.. but for some reason I don't quite follow :( When I go to the site the guy in the video goes to, it's completely different than in the vid.

---

### Post by MelDJ on 2009-12-11
the site the guy uses is just an example. it works for you source too

---

### Post by schlep3 on 2009-12-11
Ok, I guess I will try it again.

Stupid question: Where, exactly, do I go to find the pub key?

---

### Post by john newbuntu on 2009-12-11
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2ED6BB6042C24D89
```

---

### Post by schlep3 on 2009-12-12
Thanks, that worked. Now it's telling me it can't fetch a file -_-'

---

