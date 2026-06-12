---
title: "Installing Synaptic in 32-bit chroot"
date: 2006-04-14
forum: General Help
---

### Post by SimpleNL on 2006-04-14
I'm having trouble to access repositories while I am in chroot modus ("dchroot -d"), so when I run apt-get update in normal mode it hits all the repositories, but when I am in chroot mode, it doesn't resolve any of the repositories. The following is what happens...

> Do you want to continue [Y/n]? Y
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main perl-modules 5.8.7-5ubuntu1. 2

 [more of these, and same result for archive.ubuntu...]

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/x/x-common/x-common_1.08_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/x-common/x-common_1.08_all.deb)  Temporary failure resolving 'archive.ubuntu.com'

[more of these and same for security.ubuntu...]

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

(BTW, I am using [this](http://ubuntuforums.org/showthread.php?t=24575) thread as lead example, I am currently at the second step in step 5)

---

