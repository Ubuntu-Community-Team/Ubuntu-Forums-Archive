---
title: "Problem with Keys import"
date: 2010-01-04
forum: General Help
---

### Post by niteshreddy on 2010-01-04
hey guys.. i am using Karmic...

i have a problem with keys ot imported..

i am not able to install packages.. especiall from getdeb.net and so on...

here is the error..

[I][B]W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 71240B8FB3641232[/B][/I]

i dont know how to import them..

please help..

thanks..!!

---

### Post by plucky on 2010-01-04
Open a terminal and copy and paste this command into it.
```
gpg --keyserver keyserver.ubuntu.com --recv-keys A040830F7FAC5991 5A9BF3BB4E5E17B5 71240B8FB3641232
```

Good Luck

---

### Post by niteshreddy on 2010-01-04
thanks...!!:popcorn:

---

