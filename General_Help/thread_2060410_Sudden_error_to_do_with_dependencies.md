---
title: "Sudden error to do with dependencies :/"
date: 2012-09-20
forum: General Help
---

### Post by steviematt on 2012-09-20
I'm running ubuntu 12.04 64-bit and have been for the last 3 months without a problem.

Suddenly started getting this error yesterday with a no entry icon in my taskbar:

E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/mirrors.163.com_ubuntu_dists_precise-updates_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.

I also get the same problem when i run the update manager but it also tells me its an "unresolvable problem"

Also if i open software centre i got another error saying something about the wrong dependencies but now it just closes 2 seconds after i open it with no explanation...


Help...


A few days ago the update manager popped up with the usual updates. I clicked yes and install and then it said not all updates could be installed because it requires a distro update... I was like uh, what? 12.10 isn't out yet... but clicked it anyway and it proceeded to update, after it updated i checked my system and it still said 12.04.


I have no idea what happened or how this could of happened? SHould i just backup and reinstall?

I would have no problem doing this in the UK but I'm in China right now and the connection runs about as fast as a tortoise with one leg so reinstalling the updates would be a weekend job :(


EDIT:

I changed the server i get my updates from in the update manager preferences and now i get:

'W:Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages), W:Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages), E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_bumblebee_stable_ubuntu_dists_precise_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by drmrgd on 2012-09-20
Try to remove the damaged lists, and then try an update again:

```
sudo rm /var/lib/apt/lists/* -rf && sudo apt-get update
```

That should fix the merge error you're getting.  The duplicate lists error (if you're still getting that) can be fixed by looking through your sources list for duplicate entries.

---

