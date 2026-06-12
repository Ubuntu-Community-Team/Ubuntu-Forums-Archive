---
title: "Cannot reload package information. (NO_PUBKEY)"
date: 2009-07-22
forum: General Help
---

### Post by gksudo on 2009-07-22
Hello.
I never had this problem in 8.04, but now in 9.04, I get this error message after it downloads all the package information in the synaptic package manager.

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

This is very frustrating because I'm unable to get alot of the old programs I had from 8.04, such as Ogle,convert all, and so on.
Any help will be much appreciated. Thanks.

---

### Post by Rocket2DMn on 2009-07-22
You probably need to update the signatures, so we'll just reload the repository information.  From [uhelp]community/Medibuntu[/uhelp]
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by gksudo on 2009-07-22
Awesome, Thanks!

---

