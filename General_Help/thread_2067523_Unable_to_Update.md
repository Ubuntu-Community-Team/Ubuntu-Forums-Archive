---
title: "Unable to Update"
date: 2012-10-07
forum: General Help
---

### Post by ankurwidguitar on 2012-10-07
Hi!
I am unable to update Ubuntu. I am using Ubuntu 12.04 and have never been able to update it. Update manager says, 'Failed to download repository information Check your internet connection.'

I get the following in details:


```

W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/Release.gpg  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/Release.gpg  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.canonical.com/ubuntu/dists/precise/Release.gpg  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-i386/Packages  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.canonical.com/ubuntu/dists/precise/partner/binary-i386/Packages  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://dl.google.com/linux/talkplugin/deb/dists/stable/main/i18n/Translation-en  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.canonical.com/ubuntu/dists/precise/partner/i18n/Translation-en  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en  Unable to connect to 192.168.1.1:8080:
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en  Unable to connect to 192.168.1.1:8080:
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

I have tried sudo apt-get update but I get the same error.

My internet connection is fine and works perfectly.

Because of this I am unable to install any new applications from Software Center too. Any help will be appreciated.

---

### Post by sanderj on 2012-10-07
The error message says

```
Unable to connect to 192.168.1.1:8080
```

So you probably have defined a proxy server, and that is not working.

EDIT:

Oh, it is marked as "Solved"?

---

### Post by ankurwidguitar on 2012-10-08
Thank you sanderj!
I realized the proxy server issue just after I had posted this thread, that is why I marked it solved as soon as I had posted it. Anyway, thanks for your input.

---

