---
title: "Badsig"
date: 2009-07-07
forum: General Help
---

### Post by digitalbigsky on 2009-07-07
>sudo apt-get update

causes:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures were invalid: BADSIG 5A9BF3BB4E5E17B5 Launchpad PPA for chromium-daily

W: Failed to fetch [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/jaunty/Release](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/jaunty/Release)  


>gpg --keyserver subkeys.pgp.net --recv-keys 5A9BF3BB4E5E17B5
>gpg --export --armor 5A9BF3BB4E5E17B5 | sudo apt-key add -
>sudo apt-get update

Does not fix it.

---

