---
title: "Ubuntu 10.10 cannot get update"
date: 2011-03-06
forum: General Help
---

### Post by xdeathcorex on 2011-03-06
It's been a long time I haven't update my Ubuntu 10.10. This time I wanted to update it, it received some errors. Here's the details

> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 61E091672E206FF0 Launchpad nautilus-elementary
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 6E871C4A881574DE Launchpad PPA for Bisigi
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 6E871C4A881574DE Launchpad PPA for Bisigi
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG C2518248EEA14886 Launchpad VLC

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/vlmc/ubuntu/dists/maverick/Release](http://ppa.launchpad.net/webupd8team/vlmc/ubuntu/dists/maverick/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


How do I fix this?

---

### Post by krakenchaos on 2011-03-11
I'm having same error here.

```
A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release

W: Some index files failed to download, they have been ignored, or old ones used instead

```

It seems like a lot people are getting the same error.

---

### Post by wilee-nilee on 2011-03-11
For key retrieval run this.
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID

So for example the first post (first error) would be.

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192

---

### Post by apsot on 2011-09-05
> **wilee-nilee said:**
> For key retrieval run this.
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID

So for example the first post (first error) would be.

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192

didn't work for me. Any other ideas?

---

