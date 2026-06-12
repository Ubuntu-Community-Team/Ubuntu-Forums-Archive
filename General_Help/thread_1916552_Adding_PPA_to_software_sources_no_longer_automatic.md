---
title: "Adding PPA to software sources no longer automatically downloads keys"
date: 2012-01-28
forum: General Help
---

### Post by topdownjimmy on 2012-01-28
Lately, in Oneiric, adding PPAs to Software Sources doesn't automatically download the necessary key(s) anymore. After adding a PPA from Launchpad, I now frequently receive this message:

"The following signatures couldn't be verified because the public key is not available:"

followed by the key signature for the PPA.

I am able to manually add the key from the terminal with:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys

But I remember Synaptic/Software Sources used to download these keys automatically. What might be going wrong?

---

### Post by raja.genupula on 2012-01-28
> **topdownjimmy said:**
> Lately, in Oneiric, adding PPAs to Software Sources doesn't automatically download the necessary key(s) anymore. After adding a PPA from Launchpad, I now frequently receive this message:

"The following signatures couldn't be verified because the public key is not available:"

followed by the key signature for the PPA.

I am able to manually add the key from the terminal with:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys

But I remember Synaptic/Software Sources used to download these keys automatically. What might be going wrong?
The maintainer will often place a copy of the authentication key on a public key server such as [www.keyserver.net](www.keyserver.net)

I have searched and grabbed these lines from Ubuntu community . 
[https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab)

look at this . Hope that help.

---

### Post by mcduck on 2012-01-28
Using *add-apt-repository* from command line works as expected and downloads the key automatically. (I don't remember if Software Sources/Synaptic really has ever done that, although to be honest I'm not sure if I've even tried doing it that way :D)

---

