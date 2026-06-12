---
title: "Failed to 'apt-get update' new chroot environment"
date: 2010-07-25
forum: General Help
---

### Post by Ahmed Khattab Shams on 2010-07-25
:confused: :confused: :confused: :confused: Hello everybody,
while I was trying to install a chroot environment, when I try to update my apt, it replys:
> Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release](http://archive.ubuntu.com/ubuntu/dists/lucid/Release)  Unable to find expected entry  \/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.


Note: the part that says: "Unable to find expected entry  \/binary-i386/Packages in Meta-index file (malformed Release file?)"
Is their some thing wrong with the two slashes in: "\/binary-i386/"

Here's a copy of the chroot sources.list file:
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted \ universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted \ universe multiverse

I was just trying to install chroot as it documented in the Ubuntu Packaging Guide page 62:
here's a link to that Guide [http://ubuntuone.com/p/9ic](http://ubuntuone.com/p/9ic)
Thank U all

---

