---
title: "Program installation"
date: 2006-02-04
forum: General Help
---

### Post by BlackxxJapan on 2006-02-04
So far I've had linux installed for 5 hours.  Please keep that in mind even if this is a really simple problem .-.

Ok, so I finally installed Ubuntu on one of my computers, it shares with Windows 2000. It's really great so far.

I got it from a Linux magazine, it had the Breezy Badger...which I think is the latest install. Anyways, there was a second CD full of Linux programs/games/etc. I have no idea how to install the packages!

Can someone help me? I really don't mean to sound stupid, but I am very new to the Linux platform and need some help ^^"

Thanks!

---

### Post by taurus on 2006-02-04
I don't have the second CD to see exact what is the format for all those apps/games.  However, insert the second CD into the drive and wait for Gnome to mount it.  Look in there to see what are the names of the files.  I think they are probably end with deb extension and if that is the case, then you can use "dpkg -i" to install them.  Again, a little more info about the format of those files would make it much easier to show you exactly how to install them...

---

### Post by tehwa on 2006-02-04
The best way to manage software is through Synaptic. Synaptic is the "package manager" that will take care of installation/updates of software:

[https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)

You will need to add you disk to Synaptic in order to browse the software from them, the wiki article will explain how to do this. You can then use Synaptic to browse/install packages.

---

### Post by BlackxxJapan on 2006-02-09
Well, the stuff is in GZipped folders.  Do I need to unzip them?

And what ext do the packages use?  I heard it was .deb but I'm not sure.

Sorry =/

---

### Post by Mustard on 2006-02-09
It sounds like they may be tarball installations, in which case they probably all contain README files or INSTALL files with instructions for installation. You'd really be jumping in at the deep end to start with these.

I would explore using Synaptic Package Manager first, as that is the usual method for installing programs on Ubuntu.  There are over 17,000 applications in the repositories available through Synaptic which is a lot more to play with than one CD from a magazine.  Additionally, the programs in the repository are designed to work with Ubuntu without getting dependancy errors or compilation issues.

---

