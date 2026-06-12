---
title: "Updating Kernel"
date: 2009-12-04
forum: General Help
---

### Post by Baconfatty on 2009-12-04
Hey at the moment I am trying to update from 2.6.31-15-generic to 2.6.32-020632rc6-generic.

However when I go into terminal and type in

```

sudo apt-get install linux-image-2.6.32.020632rc6

```
I get

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-image-2.6.32-020632rc6-generic

```

I know the files are here [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

but don't know how to tell ubuntu where they are, can someone give me a hand here?

---

### Post by audiomick on 2009-12-04
I dare say you haven't got the location of the package included in the source list in the package manager

---

### Post by coffeecat on 2009-12-04
Simply download the deb packages linux-image* and linux-headers* for your architecture from the link and double-click on them (one at a time). The Gdebi package installer will open and install them for you. Then, if you ever need to uninstall them, they will appear in Synaptic where you can uninstall them.

By the way, there is now a rc8 version of the kernel that you want. Won't that be preferable to the rc6?

**Edit:** of course, if you want the 2.6.32 kernel updated you will have to add that PPA repository to your sources.list. Were there instructions for that in whatever howto you were using for whatever it is you are trying to achieve with a release-candidate kernel?

---

### Post by Baconfatty on 2009-12-04
well I'm using rc6 because supposedly it will allow eve to run past a splash screen, and as of yet no one has said anything about the newer release candidates.

As for the how-to I was using(which only allowed me up update to what I had) it doesn't say anything about what repository to add.

---

### Post by Zoot7 on 2009-12-04
You have to download the debs.

Say for example you want to upgrade to 2.6.32 (32 bit), go here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/)

Download the following files:

```
linux-headers-2.6.32-020632_2.6.32-020632_all.deb
linux-headers-2.6.32-020632-generic_2.6.32-020632_i386.deb	
linux-image-2.6.32-020632-generic_2.6.32-020632_i386.deb
```

Then install them in the order they're listed above by using
```
sudo dpkg -i <deb package name>
```
	
Run 
```
sudo update-grub
```
for good measure,

Reboot and select the new kernel and you're done.

Note that if you've installed an Nvidia or ATi proprietary driver, then you'll probably have to re-install it again in the new kernel.

---

### Post by Baconfatty on 2009-12-04
Thank you sir, however on a side note, using the rc6 my wireless doesn't work (which is to be expected) but also my Ethernet jack doesn't work.  Do you know where a list of drivers might be so that I can burn them to a disk and install?

---

### Post by Zoot7 on 2009-12-04
Hmm.. your ethernet connection should work from the get go. Maybe it's worth trying out the final release of 2.6.32?

---

