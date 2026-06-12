---
title: "apt-get doesn't see newer versions of packages on repository mirror"
date: 2010-02-18
forum: General Help
---

### Post by jejones3141 on 2010-02-18
To save bandwidth, I have apt-mirror running on a server so that I can install Ubuntu on a bunch of computers and get updates to them without going repeatedly to the official servers, saving me bandwidth and everyone time.

apt-mirror runs fine. There's a cron job that runs it, and it does indeed run and I can see where packages are updated, with new versions arriving. I edit /etc/apt/sources.list on the computers to look at the server instead of us.archive.ubuntu.com, and all seems well--until I notice that Update Manager isn't seeing the new versions of packages, e.g. Firefox, that I can look on the server and see are there.

I'm going to do an install on a spare machine and see whether it, starting from scratch, sees the newer version. What other things should I try? I notice that the compressed archives of the Packages files contain an updated Packages file with the newer timestamp, but the archives (Packages.{gz, bz2} don't have new timestamps... would that mislead apt-get/synaptic et al.?

[SOLVED] Wiping the mirror and repopulating it solved the problem.

---

