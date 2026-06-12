---
title: "Update Manager"
date: 2010-07-09
forum: General Help
---

### Post by ucang8me on 2010-07-09
Hi all,

I am getting an error message while updating through the Update Manager:


59 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/106MB of archives.
After this operation, 1,282kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: parse error, in file '/var/lib/dpkg/available' near line 42560 package 'gnome-power-manager':
 EOF during value of field `Original-Uploaders' (missing final newline)
E: Sub-process /usr/bin/dpkg returned an error code (2)[/I][/I]

Please let me know how to remove it?

Thanks,

---

### Post by steveneddy on 2010-07-09
In terminal do this:

```
sudo apt-get update
```

then

```
sudo apt-get upgrade
```

If you get any errors, post them here.

---

