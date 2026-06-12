---
title: "aptitude keeps trying to install old version of a package"
date: 2012-08-24
forum: General Help
---

### Post by floatingworld on 2012-08-24
So I have an installation of 12.04 LTS server and I'm working with this particular third-party app that has its own .deb repository, which I've successfully used without any issues on previous versions of Ubuntu.

But the .deb installer for the latest version crashed when I tried it and didn't install successfully.  This is evidently a known problem, per some Googling.

So I did an
```
aptitude remove packagename
```
though it didn't remove all of the pieces, so I had to delete a few directories and a user group.

I thought I'd try an older version of the package, which I've never done before and had to look up.  So I did
```
aptitude install packagename=old.version.number
```
but the older installer crashed too, so I again removed it and deleted the directories aptitude didn't remove.

But now when I do
```
aptitude install packagename
```
without any version number it's trying to install the *old* version!  I figure something is cached somewhere but I've tried these:
```
aptitude remove --purge packagename
aptitude clean
aptitude autoclean
```
to no avail, and tried the same commands with apt-get with no luck; aptitude now always tries to install the old version of the package.

And I'm noticing that when I try to install it, aptitude seems to be downloading the latest version but trying to install the older version:
```
Get: 1 http://caucho.com/download/debian/ unstable/universe resin i386 4.0.29 [23.8 MB]
Fetched 23.8 MB in 13s (1,804 kB/s)
Setting up resin (4.0.23) ...
```


So: what happened?  How do I get it to work the same way it did before I experimented with the older version?

---

### Post by floatingworld on 2012-08-24
Okay, so, for some reason the third time I tried specifying the current version like so:
```
aptitude install packagename=current.version.number
```
it actually worked when it hadn't before, dunno why.

I'm still curious if anyone knows what happened here, if there's a command that could have reset everything, and whether I'm going to have issues when a new version is released.

---

