---
title: "hold-ing a package using dpkg --set-selections"
date: 2010-10-10
forum: General Help
---

### Post by krazyd on 2010-10-10
I'm trying to install wine1.3 but I don't want the (recommended) package ttf-mscorefonts-installer.

In previous releases, I can run this to 'hold' the package and prevent it's installation:
```
echo ttf-mscorefonts-installer hold | sudo dpkg --set-selections 
```

However, this command doesn't prevent ttf-mscorefonts-installer from being installed along with wine1.3 in maverick.

```
dpkg --get-selections | grep mscore
```
and
```
dpkg --get-selections | grep hold
```
both return nothing.

However, running:
```
cat /var/lib/dpkg/status | grep -C 6 hold
```

shows that there is an entry in the dpkg status file:
> Package: ttf-mscorefonts-installer
Status: hold ok not-installed
it's just that dpkg isn't picking it up.

What is going on here, and how can I place a package on permanent hold?

Note: I ended up installing wine1.3 by running:
```
sudo aptitude install wine1.3 ttf-mscorefonts-installer**=**
```
but I don't believe that the package is actually on permanent hold.

---

### Post by krazyd on 2010-10-12
Bumping: has anyone else tried to hold a package in maverick?

---

### Post by krazyd on 2010-10-17
I just did an update and it told me this:
> The following packages will be upgraded: 
  ttf-symbol-replacement-wine1.3 wine1.3 
The following packages are RECOMMENDED but will NOT be installed:
  ttf-mscorefonts-installer

.. so it looks like aptitude does put the package on hold properly now! This never used to work, so I got used to using dpkg --set-selection, but the aptitude method is definitely much easier.

So to recap for anyone stumbling onto this thread, to place a package on hold, run 'aptitude install <pkg-name>='. For example, to install wine but not install all the microsoft fonts do:
```
sudo aptitude install wine1.3 ttf-mscorefonts-installer=
```

This will permanently place the ttf-mscorefonts-installer package on hold, even when upgrading the wine1.3 package.

---

