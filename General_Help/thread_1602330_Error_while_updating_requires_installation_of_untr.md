---
title: "Error while updating: requires installation of untrusted packages"
date: 2010-10-21
forum: General Help
---

### Post by nic-clark on 2010-10-21
Hi,

I have just started using maverick on my x61 tablet. I get this error when I try to install updates:

Requires installation of untrusted packages, and some error text underneath.

I have tried changing servers, and the same thing happens, I've updated the keys as a few were missing and they now seem to be there when I run apt-get update, the only error I get now is: 

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 4F191A5A8844C542 Launchpad PPA for xorg crack pushers

I'm not sure if this is relevant or not, but I have run out of ideaqs and can't find any more help - any suggestions appreciated!

Thanks

---

### Post by P4man on 2010-10-21
Try this
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4F191A5A8844C542
```

---

### Post by nic-clark on 2010-10-21
Thanks very much, that worked a treat!

---

