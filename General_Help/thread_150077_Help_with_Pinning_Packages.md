---
title: "Help with Pinning Packages"
date: 2006-03-25
forum: General Help
---

### Post by Bender NZ on 2006-03-25
Hihi,

I have had someone write a patch for me to php, I have run apt-get source etc and built new packages and installed them. This is all fine but now when I run apt-get upgrade it keeps wanting to upgrade libapache2-mod-php5 (I replaced these with my modifications).

I played around with some pinning settings but didn't manage to make apt stop wanting to upgrade them.

How can I make apt not upgrade any packages which I have compiled myself? Is there an option for debuild which can append my own version or could I specify my own version somewhere? (Sorry I haven't worked with source via apt before)
Presumably if I can specify my own version (ie php 5.0.5-bender) then I can pin this to be retained.

Also on a side note, I notice apt wants me to upgrade libc6 - in the past doing this on Debian has caused me huge headaches (this is a server so I will be doing this remotely), can anyone point out if I should upgrade this or not? The version shown on packages.ubuntu.com seems to be from October last year [http://packages.ubuntu.com/changelogs/pool/main/g/glibc/glibc_2.3.5-1ubuntu12/changelog](http://packages.ubuntu.com/changelogs/pool/main/g/glibc/glibc_2.3.5-1ubuntu12/changelog) so why would it only be wanting me to upgrade now? This machine was completely up to date a few days ago.

---

### Post by petervk on 2006-03-25
Example entry in /etc/apt/preferences
```

Package: *
Pin: release a=stable
Pin-Priority: 700

```

You should be able to list the packages you complied as:
```

Package: package
Pin: release a=breezy, v=versionnumber
Pin-Priority: higher then the breezy repo

```

set v to the version of the package you compiled.

you can run:
```

man apt_preferences

```
for more info.

---

