---
title: "update manager problem"
date: 2012-02-25
forum: General Help
---

### Post by bob58523 on 2012-02-25
Hi All,

When I open my update manager it says that "the package information was last updated 117 days ago" If I check my settings in package manager I get this error when I close it:

[I]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 5A5366B134BA7AE9 Launchpad GMA500 PPA
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 6AF0E1940624A220 Launchpad PPA for TualatriX
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
[/I]
Any ideas what ma be causing this and how I can fix it. I am running 32bit ubuntu 10.10 on a netbook. I have been using linux for some time, but I am by no means a pro, so I need some help :-)

thanks,
Bob

---

### Post by raja.genupula on 2012-02-25
open your terminal and do this 

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

All the best and let us know if you got any .

---

### Post by bob58523 on 2012-02-25
that worked.....

thanks for the help!!

---

### Post by raja.genupula on 2012-02-25
You're welcome . please mark the thread as solved from thread tools .

---

