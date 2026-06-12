---
title: "Updating Problem"
date: 2009-07-08
forum: General Help
---

### Post by kurt1288 on 2009-07-08
Whenever I run the Update Manager I get this error:

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7Failed to fetch [http://ppa.launchpad.net/daou/ubuntu/dists/jaunt/main/binary-i386/Packages](http://ppa.launchpad.net/daou/ubuntu/dists/jaunt/main/binary-i386/Packages)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/daou/ubuntu/dists/jaunty/main/source/Sources](http://ppa.launchpad.net/daou/ubuntu/dists/jaunty/main/source/Sources)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

What's it about and how do I fix it?

---

### Post by x33a on 2009-07-08
paste this in a terminal
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4874D3686E80C6B7
```then run
```
sudo aptitude update
```

as for the 404 error, the ppa you are using doesn't have packages for jaunty. see this:

[http://ppa.launchpad.net/daou/ubuntu/dists/](http://ppa.launchpad.net/daou/ubuntu/dists/)

---

### Post by kurt1288 on 2009-07-09
Thanks. That link just brings me to a page where I have no idea what to do. What does that mean about the PPA? Is there a way to fix it (again, if the solution is that link, I have no idea what to do).

---

### Post by drs305 on 2009-07-09
kurt1288,

Welcome to the Ubuntu forums. The link just took you to the repository you were trying to download from. Looking at that page, you can see there are feisty, gutsy and hardy links. This means those are the releases the owner is maintaining.

Launchpad hosts repositories by individuals, and this person is not currently providing packages for the jaunty release. You can try to google for another person or server that has the packages you are looking for or if you tell us the package you are looking for perhaps someone on the forum will know of a jaunty repository that carries it.

Here is some general information about how Repositories work in Ubuntu, although the wiki doesn't address your specific problem:
[Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by kurt1288 on 2009-07-09
I have no idea what package I'm looking for.

---

### Post by drs305 on 2009-07-09
> **kurt1288 said:**
> I have no idea what package I'm looking for.

At some point you added that repository. If you don't know what you want and you just want to get rid of the message, open Software Sources or Synaptic and disable the repository by going to Settings, Repositories, Third-Party tab. You will probably find the ppa listing checked. Uncheck the listing and you won't get that message any longer. Hit "Reload" on the top menu bar to update the repository listings.

If you *really* wanted to know what type of files that repository contained, you could go to the page linked earlier that showed the hardy links, and click through the subfolders until you got to the *main, multiverse, etc* folders and take a look at what is in the Packages folders.

---

### Post by kurt1288 on 2009-07-09
Thanks. I just disabled the repositories that were causing the problem.

---

