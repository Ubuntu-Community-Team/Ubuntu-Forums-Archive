---
title: "Failed to download repository info."
date: 2012-09-06
forum: General Help
---

### Post by neonick on 2012-09-06
So I have Ubuntu 12.04 installed on my laptop. My Wi-Fi works fine, aside from update problems. A red ! inside a red triangle will appear and I'll click on it and select "get updates" from the menu. It'll search and find nothing, and then I click "check" on the update page. It says it failed to download repository information and also says the package was updated XX days ago (Right now, it's at 32 days since the package information was updated). The details are limited:

W:Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Again, wi-fi works fine. I'm browsing on wi-fi right now. Thanks for the help.

---

### Post by cortman on 2012-09-06
> **neonick said:**
> So I have Ubuntu 12.04 installed on my laptop. My Wi-Fi works fine, aside from update problems. A red ! inside a red triangle will appear and I'll click on it and select "get updates" from the menu. It'll search and find nothing, and then I click "check" on the update page. It says it failed to download repository information and also says the package was updated XX days ago (Right now, it's at 32 days since the package information was updated). The details are limited:

W:Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Again, wi-fi works fine. I'm browsing on wi-fi right now. Thanks for the help.

Looks like you added some repositories that no longer exist. Run

```
gksu nautilus
```

to open Nautilus as root, then navigate to /etc/apt/sources.list.d/. Locate the files relating to the missing PPA's, and delete them. Then run

```
sudo apt-get update
```

and post back if you get any errors.

---

### Post by plucky on 2012-09-06
> W:Failed to fetch [http://ppa.launchpad.net/michael-gru...source/Sources](http://ppa.launchpad.net/michael-gru...source/Sources) 404 Not Found

See [Here](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/)

There doesn't seem to be a repository for Precise.Disable the Repository in the Other Software Tab of Software Sources.

Good Luck

---

### Post by neonick on 2012-09-08
> **cortman said:**
> Looks like you added some repositories that no longer exist. Run

```
gksu nautilus
```to open Nautilus as root, then navigate to /etc/apt/sources.list.d/. Locate the files relating to the missing PPA's, and delete them. Then run

```
sudo apt-get update
```and post back if you get any errors.


Thanks for the help. That fixed it. It was finally able to update.

---

### Post by cortman on 2012-09-08
> **neonick said:**
> Thanks for the help. That fixed it. It was finally able to update.

Great! Mark the thread [SOLVED], using the thread tools in the upper right.
Good luck!

---

