---
title: "Finding Software Sources for downloading Synaptic Package Manager"
date: 2012-08-05
forum: General Help
---

### Post by michael2009 on 2012-08-05
Until recently I was able to download the useful, but increasingly rare, Synaptic Package Manager from the Server for the UK.... I was living in the UK. However, having just moved to Indonesia, and now using a Singapore software source <http://ubuntu.oss.eznetsols.org/ubuntu>

After searching, Software Centre locates Synaptic Package Manager , but there is no 'install' button. When I press the 'more info' button, it offers to download from the 'Universe' repository. So I changed the repository and Software Centre started loading three files, two apparently for updating the cache. But after over ten minutes, there was still zero progress. Well, my USB modem is slow, but not THAT slow... 

I also tried APT, but it could not locate the package from the existing sources, so I gave up for now.  Why is it so hard to get Synaptic Package Manager, and why isn't it included in Ubuntu 12.04? I know that an awful lot of Ubuntu users over the past two years have expressed the same indignation about it being removed, so why aren't the developers listening? 

Aren't we also part of the Ubuntu Community? Or is Ubuntu turning into another faceless international body that is no longer accountable to its members and faithful supporters? I sincerely hope not, but it is a disappointing state of affairs.

---

### Post by diesch on 2012-08-05
Synaptic is still in the official *universe* software repository.  Use another server if you can't get it from *eznetsols.org*

---

### Post by ajgreeny on 2012-08-05
Make sure you have run ```
sudo apt-get update
```first.  I agree that synaptic is totally indispensable, but I can confirm that it is in the standard repos for 12.04; I have already added it to my version of 12.04.

---

### Post by Paqman on 2012-08-05
> **ajgreeny said:**
> but I can confirm that it is in the standard repos for 12.04

What do you mean by the "standard repos"? It's in Universe, which is not enabled by default but is very much an official repo, and enabling it is as simple as putting a tick in a box.

---

### Post by ajgreeny on 2012-08-06
> **Paqman said:**
> What do you mean by the "standard repos"? It's in Universe, which is not enabled by default but is very much an official repo, and enabling it is as simple as putting a tick in a box.
Sorry, but I thought universe and multiverse were enabled by default when I last installed Ubuntu 12.04.  My memory is obviously playing tricks again; not the first time either!

---

### Post by michael2009 on 2012-08-06
Thanks for all your comments :P

 I love the simplicity and style of the gnome desktop, having used it before in the UK. So earlier today I tried downloading GNOME using APT and the Singapore source repository, and it is working (only 6 hours to go!). I noticed that Synaptic is included in the GNOME package list in APT, so I am a happy bunny for nowO:)[-o<

---

