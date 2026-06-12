---
title: "Building Lucid packages on Karmic"
date: 2010-01-25
forum: General Help
---

### Post by nunyez on 2010-01-25
My reference: [https://help.ubuntu.com/community/PinningHowto#Recommended%20alternative%20to%20pinning](https://help.ubuntu.com/community/PinningHowto#Recommended%20alternative%20to%20pinning)

I want to build the latest version of rtorrent (0.8.6) on my karmic box (which has 0.8.2 in the repo).

```
sudo apt-get build-dep rtorrent
```
Does not do anything. build-dep doesnt support target release flag. Looking for a simple way to build packages from newer releases that have dependencies :(

---

### Post by nunyez on 2010-01-26
anyone?

---

### Post by ankspo71 on 2010-01-26
Hi,
Here is the homepage for rtorrent. [http://libtorrent.rakshasa.no/](http://libtorrent.rakshasa.no/)
You can build by downloading the package from there. There are instructions there too.

One of my favorite things about ubuntu, is that I can go to google.com and search for PPA's. In this case I would search for PPA rtorrent. However, I don't see any for rtorrent more recent than for Jaunty. It's a lifesaver for many other things though.
Hope this helps.

---

### Post by ankspo71 on 2010-01-26
Hi again,
[http://packages.ubuntu.com/lucid/rtorrent](http://packages.ubuntu.com/lucid/rtorrent) . You might have some luck with that link, but maybe not since you are using Karmic.

---

### Post by nunyez on 2010-01-26
> **ankspo71 said:**
> Hi again,
[http://packages.ubuntu.com/lucid/rtorrent](http://packages.ubuntu.com/lucid/rtorrent) . You might have some luck with that link, but maybe not since you are using Karmic.

Yes and you can see on that page that rtorrent has 10 dependencies. Most (if any) aren't fulfilled by karmic which means I also need those newer packages. I am not very sure if upgrading all 10 of those to lucid's versions is safe for my karmic apps (to avoid building from source).

This leaves me with only 1 option that I know of (more may be out there which is what i am hoping of):
Install all **dev** packages for rtorrent's dependencies from deb-src lucid and manually compile. **Why?** Because **sudo apt-get build-dep rtorrent**/**build-dep** does not support a flag for target release and thinks I have all of the packages needed to build rtorrent because it doesnt know I want to build lucid's version.

Help appreciated

---

