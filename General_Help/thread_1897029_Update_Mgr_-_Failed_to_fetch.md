---
title: "Update Mgr - Failed to fetch"
date: 2011-12-18
forum: General Help
---

### Post by JimS on 2011-12-18
...
Ubuntu 10.04
Triple-boot w/ Puppy & Vista
Acer laptop Extensa 4420-5237

Ran Update Manager and got the following:

Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

What does this mean?
What actions should I execute to fix?
Thanks in advance.
...

---

### Post by 2F4U on 2011-12-18
Those third party repositories you are using are not reachable. Either there is a temporary problem or they have been removed permanently. You can remove the repositories from your configuration or wait until they become available again.

---

### Post by JimS on 2012-01-03
...
I found a partial ans. in Full Circle Mag. #47 pg 32.
I ran  sudo apt-get update.
Then I went to Admin. / Software Sources and unchecked
the repository(s) that caused the error(s).

But I didn't get everything, but some is better than none.

Ran it again and here is what came up:
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
E: Some index files failed to download, they have been ignored, or old ones used instead.

I'll cold boot and see if I still get errors.
...

---

