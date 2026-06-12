---
title: "Synaptic error since official 10.10 release"
date: 2010-10-10
forum: General Help
---

### Post by XTREME DEMENTOR on 2010-10-10
Hi

Ive been running NBR 10.10RC for a few weeks and all is good.
Since the offical release and the recent update I have been getting the following error in the Synaptic package maneger when it trys to update......

[I][B]"W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead."[/B][/I]

Im noob(ish) and dont have a clue have to solve this problem.

Any help is greatly appreciated as always

Thanks

---

### Post by XTREME DEMENTOR on 2010-10-10
Sloved

In term

"sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3E5C1192"

sourced from this web page
[http://www.webupd8.org/2010/10/fix-nopubkey-error-for-extras-ubuntu.html](http://www.webupd8.org/2010/10/fix-nopubkey-error-for-extras-ubuntu.html)

---

