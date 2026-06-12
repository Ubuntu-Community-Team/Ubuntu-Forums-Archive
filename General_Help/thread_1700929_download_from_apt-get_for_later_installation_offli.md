---
title: "download from apt-get for later installation offline"
date: 2011-03-05
forum: General Help
---

### Post by UncleBoarder on 2011-03-05
I know I can build a local repository but I'd like to try just moving the appropriate .deb files.  My problem is not knowing which files I need and it what order.  example...

I want to install nfs-common

Doing apt-get install nfs-common --- does it all for me when I'm online.

So I looked in the /var/cache/apt/archives to see what was installed.  I found two nfs files...

nfs-common_1.2.0-4ubuntu4.1_amd64.deb
nfs-kernel-server_1.2.0-4ubuntu4.1_amd64.deb

But when I tried to install those on another machine I found I was missing additional files...

libgssglue1_0.1-4_amd64.deb
libnfsidmap2_0.23-2_amd64.deb
librpcsecgss3_0.19-2_amd64.deb
portmap_6.0.0-1ubuntu2.1_amd64.deb

For future installations... How do I find all the dependencies and the ORDER they need to be installed so I can write my own script and install them to a machine that is offline?

---

### Post by wojox on 2011-03-05
Read the APT section here [The Debian package management tools ]("http://www.debian.org/doc/FAQ/ch-pkgtools.en.html")  specifically apt-cache.

---

### Post by UncleBoarder on 2011-03-05
Very helpful Thanks!!

Why do all apt cache files seem to have %3a (colon) inserted into the filenames?  The same filenames seem to exist without the colon so I think this is more than just a choice of file naming structure.  I'm thinking the colon is somehow related to the installation method?

---

