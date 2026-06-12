---
title: "Error when adding mint 7 repositories to 9.04"
date: 2009-09-11
forum: General Help
---

### Post by IanB2 on 2009-09-11
I'm getting the following error message when running sudo apt-get update

Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) gloria/upstream Packages
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) gloria/import Packages
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) gloria/main Packages
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) gloria/upstream Packages
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) gloria/import Packages 
Fetched 9391B in 1s (7880B/s)                            
Reading package lists... Done
W: GPG error: [http://packages.linuxmint.com](http://packages.linuxmint.com) gloria Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3EE67F3D0FF405B2
W: You may want to run apt-get update to correct these problems

I've been trying to figure out how to fix this and am getting somewhat confused by what I've read elsewhere. There was one post which suggested that mint 7 does not have a gpg key????????

---

### Post by IanB2 on 2009-09-11
By accident I found the gpg key in the synaptic package manager. Problem solved!

---

