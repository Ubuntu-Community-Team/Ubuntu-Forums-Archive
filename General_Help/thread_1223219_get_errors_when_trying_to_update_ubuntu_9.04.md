---
title: "get errors when trying to update ubuntu 9.04"
date: 2009-07-25
forum: General Help
---

### Post by starcraftmaster on 2009-07-25
hey guys
when ubuntu is downloading all its packages to see if theirs any new ones 
most of they say Failed or Hit and some just done

what does these mean

this is the error that comes after those errors:
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources.bz2](http://au.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.

i few days ago i put a ethernet card in
and then yesterday i took it out
now am getting these errors
so any one know why ?
is their some thing i got to change back ?

---

### Post by starcraftmaster on 2009-07-27
now all it does is this :
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783


what the hell is this
is any one else getting this ?

---

### Post by credobyte on 2009-07-27
By the first, why you are using hardy mediabuntu repo ? :roll: Remove it and follow this guide: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) - it should fix your problem.

---

### Post by Soul-Sing on 2009-07-27
starcraftmaster, the medibuntukey is found in synaptic package manager in Jaunty. But first, as credobyte suggests, change the medibuntu source to Jaunty.

---

### Post by starcraftmaster on 2009-07-27
hmm 
i changed some of the settings
now its working
still a lot of the things say HIT 0KB
not sure what it means

any way
should i still do what you say to do ?
and how do i do it ?

---

### Post by starcraftmaster on 2009-08-04
should i ?

---

### Post by harry2006 on 2009-08-04
it seems to have some problem with importing the kky, try importing the keys again and see if that fixes the problem. And yes as someone already mentioned move to 9.04 repo and I guess that will fix ur problem. HTH.

---

