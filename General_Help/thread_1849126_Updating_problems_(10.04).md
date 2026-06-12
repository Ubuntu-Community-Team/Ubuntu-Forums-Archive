---
title: "Updating problems (10.04)"
date: 2011-09-23
forum: General Help
---

### Post by JusticeZero on 2011-09-23
Getting an error with sudo apt-get update. It's prevented me from getting regular updates for the past week.
At the bottom of the attempt, I get this:
> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures were invalid: BADSIG 5A9A06AEF9CB8DB0 Launchpad PPA for Ubuntu Wine Team
W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/lucid/Release](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/lucid/Release)  
W: Some index files failed to download, they have been ignored, or old ones used instead.
Any suggestions?

---

### Post by Enigmapond on 2011-09-23
I would remove that PPA from the sources list or get the public key for it from launchpad. You can still upgrade even after that error message though...easier in Synaptic...just run an update and then mark all updates and apply.

---

