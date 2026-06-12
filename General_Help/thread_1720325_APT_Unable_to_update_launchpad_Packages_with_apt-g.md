---
title: "APT: Unable to update launchpad Packages with apt-get"
date: 2011-04-03
forum: General Help
---

### Post by zefew on 2011-04-03
My Ubuntu Lucid (10.04.2) is unable to update the Packages list on launchpad.
Here is what I get:

$ sudo apt-get update
...
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
  404  Not Found   
Fetched 8707B in 3s (2243B/s)
W: Failed to fetch [http://ppa.launchpad.net/jkakavas/creepy/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/jkakavas/creepy/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

Now, I'm connected to the Internet without proxies and I can access
ppa.launchpad.net on any other tools or browsers.

It seems that the APT under my system seems to have a quite
involved configuration. So I'm hoping if any of you can point me
to any APT setting to look out for under /etc.

---

### Post by zefew on 2011-04-03
bump

---

### Post by WorMzy on 2011-04-03
The first PPA ([http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages) doesn't exist, which is why you're getting that 404; and the second 404 is occurring because the PPA manager has moved the packages from Lucid to Maverick.


I believe the file you're looking for is at /etc/apt/sources.list

```
gksu gedit /etc/apt/sources.list
```

Remove the first problem PPA, and either remove or update the second.

---

### Post by zefew on 2011-04-03
> **WorMzy said:**
> The first PPA ([http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages) doesn't exist, which is why you're getting that 404; and the second 404 is occurring because the PPA manager has moved the packages from Lucid to Maverick.


I believe the file you're looking for is at /etc/apt/sources.list

```
gksu gedit /etc/apt/sources.list
```

Remove the first problem PPA, and either remove or update the second.

'http://ppa.launchpad.net lucid/main Packages' exists. It works well on one of my other Ubuntu Lucid machines. The only different is the APT configuration.

---

### Post by QLee on 2011-04-03
zefew,
I agree with WorMzy. While those locations may have existed at some time, they aren't there now, just as your system is telling you.

---

### Post by WorMzy on 2011-04-03
> **zefew said:**
> 'http://ppa.launchpad.net lucid/main Packages' exists. It works well on one of my other Ubuntu Lucid machines. The only different is the APT configuration.

If you go to [http://ppa.launchpad.net/](http://ppa.launchpad.net/) you can see all the different PPAs. The only one with "lucid" in it's name is lucid-bleed, is this the one you're trying to use?

---

