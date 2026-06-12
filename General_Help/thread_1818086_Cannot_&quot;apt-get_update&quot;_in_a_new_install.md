---
title: "Cannot &quot;apt-get update&quot; in a new installed ubuntu 10.04 Lucid"
date: 2011-08-04
forum: General Help
---

### Post by songweijia on 2011-08-04
I installed an ubuntu 10.04 on a server. After that I use "apt-get update" with root privilige. After lines flashed for a moment, it stopped and said: 

Fetched 317B in 10s (31B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1EBA3D372A2356C9

I googled around and found many cases use "gpg" and "apt-key" to install the public key and solved the problem.

Then I
> gpg --keyserver keyserver.ubuntu.com --recv-keys 1EBA3D372A2356C9
> gpg --armor --export 1EBA3D372A2356C9 | sudo apt-key add -
things goes smooth.
then I
> sudo apt-get update

after lines went  .... it then stopped and reported:
Fetched 317B in 10s (31B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures were invalid: BADSIG 1EBA3D372A2356C9 Launchpad Nova Packages


I try to download the key from different keyserver including pgp.mit.edu, but the result are the same.

how to fix this problem?

---

