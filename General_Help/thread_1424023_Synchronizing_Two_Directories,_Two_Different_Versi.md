---
title: "Synchronizing Two Directories, Two Different Versions of Unison"
date: 2010-03-07
forum: General Help
---

### Post by jlacroix on 2010-03-07
Hello everyone. I have a home Linux network of mostly Arch machines. My wife uses Ubuntu on her Desktop. I wanted to set her up to back up to my server using Unison. (I use Unison on all of my Arch machines to keep them up to date). Unfortunately, the version of Unison in Ubuntu 9.10 is out of date compared to that of Arch, so I'm trying to find a way around this. Does anybody know?

---

### Post by flan_suse on 2010-05-16
I've tried the suggestion on this post, and it worked perfectly for me: [http://ubuntuforums.org/showthread.php?t=1449670](http://ubuntuforums.org/showthread.php?t=1449670)

From Hardy, to Intrepid, to Jaunty, to Karmic, to Lucid, the *old* stable version of Unison, version 2.27, is the only one available. This posed a problem for me since I also use openSUSE and PCLinuxOS, both of which have available Unison version 2.32.

I installed unison-gtk 2.32 from **[here]("http://packages.debian.org/squeeze/unison-gtk")**, using the .deb package for Debian Squeeze, and it runs without any problems on Lucid Lynx. I am now able to continue using Unison across all of my computers, even with the different distros.

Unfortunately, it will not install on Karmic, so your wife might have to upgrade to Lucid in order to install unison-gtk 2.32.

---

