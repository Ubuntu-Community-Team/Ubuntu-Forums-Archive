---
title: "Update Manager error"
date: 2010-01-15
forum: General Help
---

### Post by whiskeylover on 2010-01-15
Since yesterday there has been a red icon in my notification area saying "The update information may be outdated" (see attached image)

Also, when trying to use the update manager, it gives this error


> GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89Failed to fetch [http://ppa.launchpad.net/docky/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/docky/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
Is the docky URL no longer valid? Has something changed? 

Thanks

---

### Post by drs305 on 2010-01-15
To import the key, run this command:
```

gpg --keyserver keyserver.ubuntu.com --recv-keys 42C24D89 && gpg --export --armor 42C24D89 | sudo apt-key add - 

```

It does appear the docky ppa link, as entered, is dead at least for the time being.

---

### Post by whiskeylover on 2010-01-15
It looks like they replaced "docky" with "docky-main"

[http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages.gz) does appear to be a valid link. So, assuming this is the new link, where do I make these changes?

---

### Post by sliketymo on 2010-01-15
/apt/sources.list

---

### Post by whiskeylover on 2010-01-16
Sorry, I couldn't find that file. But I was able to make the change using the menu item "System/Software Sources" and now the error seems to have gone away.

Thanks for your help everybody.

p.s., Its "docky-core", and not "docky-main"

---

