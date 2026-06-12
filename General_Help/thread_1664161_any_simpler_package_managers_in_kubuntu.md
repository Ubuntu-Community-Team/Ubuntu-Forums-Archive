---
title: "any simpler package managers in kubuntu?"
date: 2011-01-10
forum: General Help
---

### Post by Seepgood on 2011-01-10
I have been using kubuntu 10.04 for a while now and its working great. The main problem is that as far as I know it lacks a simplified package manager like ubuntu software center. Kpackagekit is fine as a synaptic replacement but searching for programs among all sorts of unrelated packages is very tiring. Are there any other options?

---

### Post by ean5533 on 2011-01-10
I agree with you, KPackageKit works, but it isn't nice to use. Luckily, there's no reason you can't just install the Ubuntu Software Center like I did. I believe the package name is software-center, so:

```
sudo apt-get install software-center
```

The drawback to this is that you'll have to install GTK library dependencies, but it should only be about 50MB if I remember correctly. As I mentioned, I use Software Center on Kubuntu and it works just fine.

---

### Post by ajgreeny on 2011-01-10
As does synaptic itself, which as far as I'm concerned, has not yet been beaten as a package manager.

---

### Post by ankspo71 on 2011-01-12
Hi,
I think "Muon" is also nice substitute for kpackagekit, but it will need a bit more features before it will be better than "Ubuntu Software Center" or "Synaptic Package Manager". Muon is a pretty nice package management application for KDE though. As the others have said, software-center and synaptic can easily be installed in the KDE desktop.

You can find muon in the Ubuntu's repositories (in maverick and natty), or you can check for later versions at this PPA repository: [https://edge.launchpad.net/~echidnaman/+archive/qapt/](https://edge.launchpad.net/~echidnaman/+archive/qapt/) (maverick and lucid)

---

### Post by Seepgood on 2011-01-18
I've installed ubuntu software center for now, but I will also try muon and the other suggestions. Thanks for the replies everyone.

---

