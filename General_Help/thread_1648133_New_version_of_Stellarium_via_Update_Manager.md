---
title: "New version of Stellarium via Update Manager"
date: 2010-12-18
forum: General Help
---

### Post by marcething on 2010-12-18
Hi, 

I'm using Ubuntu 10.4 because I don't like "mickey mouse soft" xp vista or what have you.
I have a practical question:
As amateur astronomer, I like very much Stellarium.
I installed this from the Ubuntu Software Centre, without any problem, of course.
The version in the software centre is 0.10.4.
The last version on the Stellarium Website is 0.10.6.

You can download this as a tarball, but then you have to compile it, i guess.

Is there a way to get the latest version in the software centre, or have it updated via update manager?
Many thanks in advance for your guys help

Best regards

Marc

---

### Post by jmszr on 2010-12-18
marcething,

You can download the .deb's for 10.6 Stellarium from here: [https://launchpad.net/~stellarium/+archive/stellarium-releases/+sourcepub/1385966/+listing-archive-extra](https://launchpad.net/~stellarium/+archive/stellarium-releases/+sourcepub/1385966/+listing-archive-extra) .

You will need to install the stellarium-data all.deb first and then the i386 or amd64 .deb .
The GDebi Package Installer should automatically install the .deb's when you download them.

I just updated Stellarium myself and this works fine. I did use the Synaptic Package Manager to uninstall Stellarium 10.4 first. Although I don't know whether that is necessary, it certainly doesn't hurt. 

Hope that helps.

---

### Post by cgroza on 2010-12-18
> **jmszr said:**
> marcething,
Although I don't know whether that is necessary, it certainly doesn't hurt. 

Hope that helps.

It is not necessary, dpkg takes care of it itself.

---

### Post by jmszr on 2010-12-18
cgroza,

Good to know, thanks.

---

### Post by mcduck on 2010-12-18
Better yet, instead of downloading that package and installing it, you could add the PPA repository (and get the latest package and updates as well).

[https://launchpad.net/~stellarium/+archive/stellarium-releases]("https://launchpad.net/~stellarium/+archive/stellarium-releases")

```
sudo add-apt-repository ppa:stellarium/stellarium-releases
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Jahid65 on 2010-12-18
You need to add ppa in software source.Write these commands in terminal.
```
sudo add-apt-repository **ppa:stellarium/stellarium-releases**
sudo apt-get update

```
You will stellarium update in update manager or synaptic manager.

---

### Post by marcething on 2010-12-19
Super!!!
Works like a charm!!!

Thanks a lot guys

Best regards

Marc

---

