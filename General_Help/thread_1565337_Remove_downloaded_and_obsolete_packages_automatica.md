---
title: "Remove downloaded and obsolete packages automatically"
date: 2010-08-31
forum: General Help
---

### Post by rbutler on 2010-08-31
Hi there,

My netbook has only 100MB of space left. On the long run this is not a problem and I certainly want to stay with ubuntu netbook distro.
But every time I update it I run into space issues, because of the downloaded packages. What would be the command to remove all downloaded packages?
As well, in case a new kernel is downloaded it is kept installed till I explicitly remove it. Can this be changes in a sense that the old one is removed as soon as I reboot with the new one?

Thanks,
Ralf

---

### Post by inameiname on 2010-08-31
This will clean things up a bit. I also suggest to install bleachbit, as it will do this and much, much more.

sudo apt-get install localepurge deborphan

sudo apt-get -y autoclean && sudo apt-get -y autoremove && sudo apt-get -y clean && sudo apt-get -y remove && sudo deborphan | xargs sudo apt-get -y remove --purge


sudo apt-get install bleachbit

..if desire.

And as for removing kernels automatically, you could set up a script to do it, using this terminal command:

sudo apt-get remove --purge 2.6.XX-XX-*

...where you write in the old kernel that isn't running on reboot. I wouldn't suggest doing it automatically, as that can be dangerous.

Or, for kernel removal, also install ubuntu-tweak, as it has an easy gui to remove kernels.

---

### Post by TimEnid on 2010-08-31
Download UbuntuTweak. THis will help remove obsolete files.

---

### Post by hhh on 2010-08-31
I don't think removing stuff automatically is the way to go as stuff can get thrown out that you need (Computer Janitor and sudo apt-get --purge autoremove are good at this!), but see this post...
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

Be warned, the post is from 2007 and each new release of Ubuntu renders some of the old documentation incorrect/obsolete, but that post looks OK as there are no comments saying "YOU HOSED MY SYSTEM!!!".

---

