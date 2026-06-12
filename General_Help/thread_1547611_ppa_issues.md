---
title: "ppa issues"
date: 2010-08-07
forum: General Help
---

### Post by gsgleason on 2010-08-07
I am reloading my xbmc box on top of a minimal ubuntu installation.  I have added the following ppas:

ppa:nvidia-vdpau/ppa
ppa:team-xbmc-svn/ppa

When I do sudo apt-get update, however, I get these errors near the end:

```

Hit http://mirrors.kernel.org karmic-updates/restricted Sources
Hit http://mirrors.kernel.org karmic-updates/universe Packages
Hit http://mirrors.kernel.org karmic-updates/universe Sources
Hit http://mirrors.kernel.org karmic-updates/multiverse Packages
Hit http://mirrors.kernel.org karmic-updates/multiverse Sources
Err http://ppa.launchpad.net karmic/main Packages
  404  Not Found [IP: 204.152.191.39 80]
Err http://ppa.launchpad.net karmic/main Packages
  404  Not Found [IP: 204.152.191.39 80]
W: Failed to fetch http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found [IP: 204.152.191.39 80]

W: Failed to fetch http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found [IP: 204.152.191.39 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

However, I can wget the same file immediately afterward:
```

gsg@xbmc ~
$ wget http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz
--2010-08-06 22:09:35--  http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz
Resolving ppa.launchpad.net... 91.189.90.217
Connecting to ppa.launchpad.net|91.189.90.217|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 12249 (12K) [application/x-gzip]
Saving to: `Packages.gz'

100%[======================================>] 12,249      42.0K/s   in 0.3s    

2010-08-06 22:09:36 (42.0 KB/s) - `Packages.gz' saved [12249/12249]

```

What gives?  When I do a dns lookup for ppa.launchpad.net, it resolves to 91.189.90.217, just like wget shows.  Where is that ip address coming from in the apt-get update failure?

update:

the ip address resolves to part of kernel.org, the mirror I have set for the normal ubuntu stuff.  Why would me extra repo in /etc/apt/sources.list.d/ be using that instead of the actual hostname?

---

### Post by gsgleason on 2010-08-07
Damn it.  I figured it out.  Somehow I had a file /etc/apt/apt.conf that was telling it to use my mirror as a proxy!!  WtF!!

Fixed.  Thanks anyway.

---

