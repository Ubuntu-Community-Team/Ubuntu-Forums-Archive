---
title: "Making your own repo"
date: 2010-11-11
forum: General Help
---

### Post by lukemk1 on 2010-11-11
Okay, this is just an idea I'm wanting to know if it is possible so I'm looking for advice on this. 

I was wondering how easy it would be to basically make your own home server that acts as a repo for all of your applications that you install by downloading them from the source and then placing them onto the server. That way if the repo goes down for some reason and you need to do a fresh install you don't have to worry.

Is this a plausible idea or would I never need to worry about repos going down?

---

### Post by matt_symes on 2010-11-11
Hi

Does this help?

[https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)

Kind regards

---

### Post by lukemk1 on 2010-11-11
Thanks, that looks like it would be what I'm looking for.

---

### Post by lukemk1 on 2010-11-11
One other question. Say you update an application does the apt-cache server update the app in its database to the newest version as well?

---

### Post by Cheesehead on 2010-11-11
Reposities tend to be quite reliable. And there are many of them.

So unless you are caching a repo to save bandwidth on your large network's gateway or to serve custom packages, setting up a personal mirror is just a fun disk-filling hobby.

In fact, you don't even need a mirror at all. Using the debtorrent or apt-p2p packages, you can use torrent-based packages - your primary 'mirror' is the cloud of other users /var/apt/caches, with a fallback to existing mirrors.

Using caching software: When the cache manager receives a request for a package that it has, it serves the package. If the cache does not have the package (or version), the cache manager gets the new package, then serves it. The cache manager normally does not delete the old version. It's up to your package manager to request the correct version - package managers are very good at requesting the correct version.

---

### Post by lukemk1 on 2010-11-12
When you say they are reliable does that mean I really don't have to take the time to worry about setting up something like an apt-cache server then? And do repos still keep packages for distributions even after they have reached their end of life?

---

### Post by James78 on 2010-11-12
This might help you out some.
[http://nerdica.com/?p=43](http://nerdica.com/?p=43)

---

