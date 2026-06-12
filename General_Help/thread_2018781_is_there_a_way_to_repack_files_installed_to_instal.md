---
title: "is there a way to repack files installed to install on another os?"
date: 2012-07-06
forum: General Help
---

### Post by slixz85 on 2012-07-06
hi. i have an offline computer with alot of files on it and the offline computer has no way of getting online. there are a ton of programs installed on it. i am wondering if there is a program or something useful i can download and install on it by a usb flash drive that could possibly like repack the files that are installed back into a single .deb files or such and be able to install it on the other os (the offline machine has three os's on it. i just need to transfer these programs over to another partition)?
thanks to any help

---

### Post by 1clue on 2012-07-06
If you're talking about 3 other computers with exactly the same version of the same distribution on it, and all pretty similar hardware, then what you're proposing is feasible.

If you're talking about, say, Suse, Ubuntu, Gentoo then you'll have problems.  Debian and Ubuntu are somewhat interchangeable but not completely, and switching distros is pretty much a guaranteed fail.

The best thing I can think of, if you have a nice and big, nice and speedy box, is to install a virtualization server on one of them (VMware or KVM or similar) and then suck the image from the old box into the other box.  In that case, you can scan the entire disk and make a sort-of clone of that box.

All I've actually tried that with is VMware, which has a converter to scan your disk and transfer it to an image on another drive.

---

### Post by Cheesehead on 2012-07-06
Try the apt-zip package. 
Or Synaptic's 'generate a package download script' feature.
Or simply copy-and-paste the package list from apt-get.

For example, let's say I want to install gedit onto my offline system.

Step 1: On the offline system, find out which packages you need to install.
```
$ sudo apt-get --simulate install gedit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gedit-common gir1.2-gtksource-3.0 libgtksourceview-3.0-0
  libgtksourceview-3.0-common
[COLOR="Red"]The following NEW packages will be installed:
  gedit gedit-common gir1.2-gtksource-3.0 libgtksourceview-3.0-0
  libgtksourceview-3.0-common[/COLOR]
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.

```

Step 2: On the online system, download the packages.

Step 3: On the offline system, copy the new packages into /var/cache/apt/archives/
Then apt-get install gedit for real. The system should automatically detect all the relevant packages in the archive.

---

### Post by slixz85 on 2012-07-06
> **1clue said:**
> If you're talking about 3 other computers with exactly the same version of the same distribution on it, and all pretty similar hardware, then what you're proposing is feasible.

If you're talking about, say, Suse, Ubuntu, Gentoo then you'll have problems.  Debian and Ubuntu are somewhat interchangeable but not completely, and switching distros is pretty much a guaranteed fail.

The best thing I can think of, if you have a nice and big, nice and speedy box, is to install a virtualization server on one of them (VMware or KVM or similar) and then suck the image from the old box into the other box.  In that case, you can scan the entire disk and make a sort-of clone of that box.

All I've actually tried that with is VMware, which has a converter to scan your disk and transfer it to an image on another drive.
ok thanks for the suggestion i haven't ever tried any vmware before though. you just refreshed my mind though. would that remastersys program or similar work to just copy my whole os and be able to reinstall it on the other partition instead? i was actually trying to do this the other way i mention above because the other partition i want to install stuff to has 12.04 and this i am using now is 10.04. and yes all the three partitions are ubuntu deriv.
thanks

---

### Post by slixz85 on 2012-07-06
> **Cheesehead said:**
> Try the apt-zip package.

i just installed apt-zip however not ever been great with commands. i am already lost lol

---

### Post by slixz85 on 2012-07-06
> **Cheesehead said:**
> Try the apt-zip package. 
Or Synaptic's 'generate a package download script' feature.
Or simply copy-and-paste the package list from apt-get.

For example, let's say I want to install gedit onto my offline system.

Step 1: On the offline system, find out which packages you need to install.
```
$ sudo apt-get --simulate install gedit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gedit-common gir1.2-gtksource-3.0 libgtksourceview-3.0-0
  libgtksourceview-3.0-common
[COLOR="Red"]The following NEW packages will be installed:
  gedit gedit-common gir1.2-gtksource-3.0 libgtksourceview-3.0-0
  libgtksourceview-3.0-common[/COLOR]
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.

```

Step 2: On the online system, download the packages.

Step 3: On the offline system, copy the new packages into /var/cache/apt/archives/
Then apt-get install gedit for real. The system should automatically detect all the relevant packages in the archive.


thanks alot to you guys. this helps out alternatively as well. i actually did install remastersys-gui and it appears to be what i need i just gotta buy a new flash drive now as mine is 2gb and i am sure it will far exceed that now. thanks again

---

