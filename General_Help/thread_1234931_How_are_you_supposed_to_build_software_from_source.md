---
title: "How are you supposed to build software from source?"
date: 2009-08-08
forum: General Help
---

### Post by nbv4 on 2009-08-08
I have been using qbittorrent for a while now and I really like it. I wanted toi try out the new 1.4.0 release candidate, but since it was only realeased a few days ago, I know my only option was to build from source. No big deal I've done this before.

I first uninstall 1.3.3 from synaptic. Then I download the tar.bz from the qbittorrent site. I unzip, then run ./configure. I get an error saying I need to have libtorrent-rasterbar with a version higher than 0.14.0. I look in synaptic, and I see I have libtorrent-rasterbar installed, version "0.14.2-2ubuntu1". I guess since that "2ubuntu1" thing in the version string is what is making the script think I don't have it installed.

So I then compile the latest version of libtorrent-rasterbar, then try qbittorrent again. Now when I try to ./configure, I get this error: "Error: need libcurl!". Again, synaptic says I have libcurl version "7.18.2-8ubuntu4". At that point I gave up.

Is there a better way to do this? IS there any way to get these programs to use the repo version of these libraries?

---

### Post by michy99 on 2009-08-08
The problem is probably that you are missing the header files, not the libraries themselves. Usually the packages needed for compiling programs contain 'dev' in the name. In this case, libtorrent-rasterbar-dev and libcurl4-gnutils-dev.

---

### Post by oldos2er on 2009-08-08
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by nbv4 on 2009-08-08
> **michy99 said:**
> The problem is probably that you are missing the header files, not the libraries themselves. Usually the packages needed for compiling programs contain 'dev' in the name. In this case, libtorrent-rasterbar-dev and libcurl4-gnutils-dev.

o wow that was it, thanks!

---

