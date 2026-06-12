---
title: "Updates say repository doesn't work"
date: 2009-09-23
forum: General Help
---

### Post by justin.rixx on 2009-09-23
So I went to update my Jaunty machine, and it said something about one of the reposotories not being available. It has done this for the past week or so, but I'm not sure if this is going to make me miss some important security updates or what. I did add a couple repositories, Chromium was one, and the other I used to download some themes.

I have attached a screenshot of when it did it.

[ATTACH]129517[/ATTACH]

The text in the box says:

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/jaunty/Release](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/jaunty/Release)  Unable to find expected entry  maindeb-src/binary-amd64/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

If this is a big deal, please let me know and tell me how to fix it(if I can fix it).

Thanks much!

-Justin

---

### Post by t0p on 2009-09-23
It seems that the repository is offline.  It's not one of the major repos (ie it's not main, universe, multiverse etc) - it's a PPA.  To find out which one, check your Sources List file (/etc/apt/sources.list).  Once you know which application(s) it's for, you'll be able to assess what kind of risk this represents.

---

### Post by justin.rixx on 2009-09-23
Yeah, it looks like it's just the one I used to get some themes. Thanks!

---

